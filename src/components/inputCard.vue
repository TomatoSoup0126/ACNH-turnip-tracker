<template>
  <div class="col-2">
   
        <div class="card-header">
          {{day.name}}
        </div>
        <ul class="list-group list-group-flush">
          <li class="list-group-item">
            <label>上午</label> 
            <input type="text" class="form-control" placeholder="$" :id="day.id">
          </li>
          <li class="list-group-item">
             <label>下午</label> 
            <input type="text" class="form-control" placeholder="$" :id="day.id">
          </li>
        </ul>

  </div>
</template>

<script>
export default {
  props:{
    day: {
      type: Array,
      required: true
    }
  }

  
}
</script>