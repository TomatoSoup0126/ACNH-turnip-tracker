<template>
  <div id="app">
    <navbar />
    <div class="container mt-3">
      <div class="row">
        <div class="col-4">

          <div class="input-group mb-3 ml-4">
            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">週日買入價格</span>
            </div>
            <input type="number" class="form-control" placeholder="＄" v-model.number="purchasePrice">
          </div>

        </div>

        <div class="col-8 pt-2">
            <h5>{{prediction}}</h5>
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
                <input type="number" class="form-control" placeholder="$" v-model="chartData.rows[i*2]['價錢']">
              </li>
              <li class="list-group-item">
                <label>下午</label> 
                <input type="number" class="form-control" placeholder="$" v-model="chartData.rows[i*2+1]['價錢']">
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
    },

    prediction: function(){

      if (this.chartData.rows[0]['價錢'] === ''){

        return '請輸入買入/賣出價格開始進行預測...'

      }else{
        
        let startPercent = this.chartData.rows[0]['價錢']/this.purchasePrice

        if (startPercent > 0.9) {
          return '可能為波形、三期型或四期型'
        } else if(startPercent > 0.85 && startPercent < 0.9){
          return '可能為三期型、四期型或遞減型'
        } else if(startPercent > 0.8 && startPercent < 0.85){
          return '可能為四期型'
        } else if(startPercent > 0.6 && startPercent < 0.8){
          return '可能為波型或四期型'
        } else {
          return '可能為四期型'
        }
          
      }

    }

  },

  data() {
    
    this.yaxis = {
        max: 700
      }


    return {

    purchasePrice:'',

    input: [],

    patten:[],
    
    chartData: {
      columns: ['日期', '價錢'],
      rows: [
        { '日期': '週一上午', '價錢': '' },
        { '日期': '週一下午', '價錢': '' },
        { '日期': '週二上午', '價錢': '' },
        { '日期': '週二下午', '價錢': '' },
        { '日期': '週三上午', '價錢': '' },
        { '日期': '週三下午', '價錢': '' },
        { '日期': '週四上午', '價錢': '' },
        { '日期': '週四下午', '價錢': '' },
        { '日期': '週五上午', '價錢': '' },
        { '日期': '週五下午', '價錢': '' },
        { '日期': '週六上午', '價錢': '' },
        { '日期': '週六下午', '價錢': '' }
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
