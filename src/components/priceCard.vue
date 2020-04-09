<template>
  <div class="card col-12">
    <div class="card-body row">
      <inputCard 
        v-for="day in weekday" 
        :key="day.id"
        :day="day"
      />
      
    </div>

  </div>
</template>

<script>
import inputCard from '../components/inputCard.vue'

export default {
  components:{
    inputCard
  },

  data() {
    return {
      weekday:[
        {
          name:'週一',
          id:1
        },

        {
          name:'週二',
          id:2
        },

        {
          name:'週三',
          id:3
        },

        {
          name:'週四',
          id:4
        },

        {
          name:'週五',
          id:5
        },

        {
          name:'週六',
          id:6
        },

      ]
    }
    
  }
  
}
</script>