<template>
  <div id="app">
    <navbar />
    <div class="container mt-3">
      <div class="col-4">

        <div class="input-group mb-3 ml-4">
          <div class="input-group-prepend">
            <span class="input-group-text" id="basic-addon1">週日買入價格</span>
          </div>
          <input type="number" class="form-control" placeholder="＄" v-model.number="purchasePrice">
        </div>

      </div>

      <div class="card col-12">
     
        <div class="card-body row">
          <div class="col-2" v-for="(day,i) in getWeek" :key="day">
            
            <div class="card-header">
              {{day}}
            </div>
            <ul class="list-group list-group-flush">
              <li class="list-group-item">
                <label>上午</label> 
                <input type="number" class="form-control" placeholder="$" v-model="input[i*2+1]">
              </li>
              <li class="list-group-item">
                <label>下午</label> 
                <input type="number" class="form-control" placeholder="$" v-model="input[i*2+2]">
              </li>
            </ul>

          </div>
        </div>

      </div>

      <ve-line :y-axis="yaxis" :data="chartData" class="mt-3"></ve-line>
    </div>

    
  </div>
</template>

<script>
import 'bootstrap'
import 'bootstrap/dist/css/bootstrap.min.css'
import moment from 'moment'
import navbar from './components/navbar.vue'
import VeLine from 'v-charts/lib/line'

export default {
  name: 'App',
  components: {
    navbar,
    VeLine
    
  },

  computed:{
    getWeek: function(){
      const currentWeek = []

      for (let i = 1; i < 7; i++) {
        currentWeek.push(moment().weekday(i).format('MMDD ddd'))
      }

      return currentWeek
    }

  },

  data() {
    
    this.yaxis = {
        max: 700
      }

    this.chartSettings = {

        dataType: function (v) {
          return '$' + v
        }
      }

    return {

    purchasePrice:'',

    input: [],

    patten:[],
    

    chartData: {
      columns: ['日期', '賣價'],
      rows: [
        { 
          '日期': '週一 AM', 
          '賣價': 0 
        },

        { 
          '日期': '週一 PM', 
          '賣價': 0 
        },

        { 
          '日期': '週二', 
          '賣價': 0 
        },

        { 
          '日期': '週四',
          '賣價': 0 
        },

        { 
          '日期': '週五',
          '賣價': 0 
        },

        { 
          '日期': '週六',
          '賣價': 0 
        }
      ]
    }
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
