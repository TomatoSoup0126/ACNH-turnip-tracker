<template>
  <div id="app">
    <navbar />
    <div class="container mt-3">
      <purchaseCard />
      <div class="card col-12">
     
      <div class="card-body row">
        <inputCard 
          v-for="day in weekday" 
          :key="day.id"
          :day="day"
        />
      </div>

  </div>
    </div>
   

  </div>
</template>

<script>
import 'bootstrap'
import 'bootstrap/dist/css/bootstrap.min.css'
import navbar from './components/navbar.vue'
import inputCard from './components/inputCard.vue'
import purchaseCard from './components/purchaseCard'

export default {
  name: 'App',
  components: {
    navbar,
    inputCard,
    purchaseCard
    
  },

  data() {
    return {
    purchasePrice:0,

    weekday:[
      {
        name:'週一',
        id:1,
        price:0
      },

      {
        name:'週二',
        id:2,
        price:0
      },

      {
        name:'週三',
        id:3,
        price:0
      },

      {
        name:'週四',
        id:4,
        price:0
      },

      {
        name:'週五',
        id:5,
        price:0
      },

      {
        name:'週六',
        id:6,
        price:0
      },

    ]
  }
    
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
