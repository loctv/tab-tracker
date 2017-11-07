<template>
  <b-navbar toggleable="md" type="light" variant="light">
    <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>

    <b-navbar-brand href="#" @click="navigateTo({name: 'root'})">Tab Tracker</b-navbar-brand>

    <b-collapse is-nav id="nav_collapse">

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto" right>
        <b-nav-item 
          @click="navigateTo({name: 'login'})" 
          v-if="!$store.state.isUserLoggedIn">Log in</b-nav-item>
        <b-nav-item 
          @click="navigateTo({name: 'register'})" 
          v-if="!$store.state.isUserLoggedIn">Sign Up</b-nav-item>
        <b-nav-item 
          @click="logout" 
          v-if="$store.state.isUserLoggedIn">Log Out</b-nav-item>
      </b-navbar-nav>

    </b-collapse>
  </b-navbar>
</template>

<script>
export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    },
    logout () {
      this.$store.dispatch('setToken', null)
      this.$store.dispatch('setUser', null)
      this.$router.push({
        name: 'root'
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
