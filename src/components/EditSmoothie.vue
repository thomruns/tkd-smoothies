<template>
  <div v-if="smoothie" class="edit-smoothie container">
    <h2>Edit {{ smoothie.title }}</h2>
    <p>Ingredients: {{ smoothie.ingredients }}</p>
    <p>Slug: {{ smoothie.slug }}</p>
    <p>Document ID: {{ smoothie.id }}</p>
  </div>
</template>

<script>
import db from '@/firebase/init' //import the Firebase database

export default {
  name: 'EditSmoothie',
  data() {
    return {
      smoothie: null
    }
  },
  created() {
    let ref = db.collection('smoothies').where('slug', '==', this.$route.params.smoothie_slug)
    ref.get().then(snapshot => {
      snapshot.forEach(doc => {
        this.smoothie = doc.data()
        this.smoothie.id = doc.id
      })
    })
  }
}
</script>

<style>

</style>

