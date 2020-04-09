<template>
  <div id="app">
    <navbar />
    
    <img alt="Vue logo" src="./assets/logo.png">
   
    <priceCard />
  </div>
</template>

<script>
import 'bootstrap'
import 'bootstrap/dist/css/bootstrap.min.css'
import navbar from './components/navbar.vue'
import priceCard from './components/priceCard.vue'

export default {
  name: 'App',
  components: {
    navbar,
    priceCard
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
