<template>
  <div id="app">
    <page-header />
    <b-container fluid id="main">
      <!-- <img src="./assets/logo.png"> -->
      <router-view/>
    </b-container>
  </div>
</template>

<script>
import PageHeader from '@/components/Header'
export default {
  name: 'app',
  components: {
    PageHeader
  }
}
</script>


<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#main {
  margin-top: 18px;
}
</style>
