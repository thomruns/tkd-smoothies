<template>
  <div class="index">
    <h1>{{ msg }}</h1>
    <p>This project uses {{ useCss }} for styling.</p>
  </div>
</template>

<script>
export default {
  name: 'Index',
  data () {
    return {
      msg: 'Just placeholder text',
      useCss: 'Materialize'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
