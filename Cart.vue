<template>
  <div>
    
    
    
    <div class="d-grid gap-2">
            <button class="btn btn-primary" type="button" @click="productBtnClicked">Go To Products</button>
    </div>
    <div v-for="product in cart" :key="product.product_name" > 
        <div class="card" style="width: 18rem;">
        <img src="" class="card-img-top" alt="">
        <div class="card-body">
            <h5 class="card-title">{{product.product_name}}</h5>
            <p class="card-text">{{product.currency_sign}}{{product.cost}}</p>
        </div>
        </div>
    </div>
      
      
      

  </div>
</template>

<script>
export default {
  name: 'Cart',
  props: {
      cart:Array,
  },
  data(){
      return {
      }
  },
  methods:{
      productBtnClicked(){
          this.$emit("goToPage","listing")
      }


  }
}
</script>
<style>

</style>


