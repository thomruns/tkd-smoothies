<template>
  <div class="add-smoothie container">
    <h2 class="center-align green-text text-darken-2">Add new smoothie recipe</h2>
    <form @submit.prevent="AddSmoothie">
      <div class="field title">
        <label for="title">Smoothie Name</label>
        <input type="text" name="title" v-model="title">
      </div>
      <div v-for="(ing, index) in ingredients" :key="index" class="field">
        <label for="ingredient">Ingredients:</label>
        <input type="text" name="ingredient" v-model="ingredients[index]">
        <i class="material-icons delete" @click="deleteIng(ing)">delete</i>
      </div>
      <div class="field add-ingredient">
        <label for="add-ingredient">Add an ingredient, (press Tab key to add another)</label>
        <input type="text" name="add-ingredient" @keydown.tab.prevent="addIng" v-model="another">
      </div>
      <p v-if="feedback" class="red-text">{{ feedback }}</p>
      <div class="field center-align">
        <button class="btn purple darken-1">Add Smoothie</button>
      </div>
    </form>
  </div>
</template>

<script>
import db from '@/firebase/init'  // add the Firebase database
import slugify from 'slugify' // package to create slug

export default {
  name: 'AddSmoothie',
  data() {
    return {
      title: null,
      another: null,
      ingredients: [],
      feedback: null,
      slug: null
    }
  },
  methods: {
    AddSmoothie() {
      if(this.title) {
        this.feedback = null
        // create slug using slugify package
        this.slug = slugify(this.title, {
          replacement: '-',
          remove: /[$*_+~.()'"!\-:@]/g,
          lower: true
        })
        db.collection('smoothies').add({
          title: this.title,
          ingredients: this.ingredients,
          slug: this.slug,
        }).then(() => {
          this.$router.push({ name: "Index" })
        }).catch(err => {
          console.log(err)
        })
      } else {
        this.feedback = "You must enter a smoothie title"
      }
    },
    addIng() {
      if(this.another) {
        this.ingredients.push(this.another)
        //console.log(this.ingredients)
        this.another = null
        this.feedback = null
      } else {
        this.feedback = 'Please enter a value to add an ingredient'
      }
    },
    deleteIng(ing) {
      this.ingredients = this.ingredients.filter(ingredient => {
        return ingredient != ing
      })
    }
  }
}
</script>

<style>
.add-smoothie {
  margin-top: 60px;
  padding: 20px;
  max-width: 500px;
}

.add-smoothie h2 {
  font-size: 2em;
  margin: 20px auto;
}

.add-smoothie .field {
  margin: 20px auto;
  position: relative;
}

.add-smoothie button {
  border-radius: 8px;
}
.add-smoothie .delete {
  position: absolute;
  right: 0;
  bottom: 16px;
  color: #aaa;
  font-size: 1.4em;
  cursor: pointer;
}
</style>


