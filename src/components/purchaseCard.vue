<template>
  <div class="col-4">

      <div class="input-group mb-3 ml-4">
        <div class="input-group-prepend">
          <span class="input-group-text" id="basic-addon1">週日買入價格</span>
        </div>
        <input type="number" class="form-control" placeholder="＄" v-model="purchasePrice">
      </div>

      <!-- <h3>input is {{purchasePrice}}</h3> -->

  </div>
</template>

<script>
export default {
  props:{
    purchasePrice:{
      type: Number,
      required: true
    }
  }
}
</script>