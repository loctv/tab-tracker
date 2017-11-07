<template>
  <b-navbar toggleable="md" type="light" variant="light">
    <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>

    <b-navbar-brand href="#" @click="navigateTo({name: 'home'})">Tab Tracker</b-navbar-brand>

    <b-collapse is-nav id="nav_collapse">

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto" right>
        <b-nav-item 
          @click="navigateTo({name: 'login'})" 
          v-if="!$store.state.isUserLoggedIn">Login</b-nav-item>
        <b-nav-item 
          @click="navigateTo({name: 'register'})" 
          v-if="!$store.state.isUserLoggedIn">Sign Up</b-nav-item>
      </b-navbar-nav>

    </b-collapse>
  </b-navbar>
</template>

<script>
export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
