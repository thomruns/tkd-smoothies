<template>
  <div class="navbar">
    <nav class="nav-extended green darken-2">
      <div class="nav-content">
        <router-link to="">
          <span class="nav-title">Green Smoothies</span>
        </router-link>
        <a href="" class="btn-floating btn-large halfway-fab purple darken-1">
          <router-link to="">
            <i class="material-icons">add</i>
          </router-link>
        </a>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  data() {
    return {

    }
  }
}
</script>

<style>
  .navbar nav {
    padding: 0 20px;
  }
</style>

