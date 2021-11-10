<template>
  <div class="hello">
    
        <div class="d-grid gap-2">
            <button class="btn btn-primary" type="button" @click="cartBtnClicked">Go To Cart</button>
        </div>
        <div v-for="product in products" :key="product.product_name"> 
        <div class="card" style="width: 18rem;">
        <img src="" class="card-img-top" alt="">
        <div class="card-body">
            <h5 class="card-title">{{product.product_name}}</h5>
            <p class="card-text">{{product.currency_sign}}{{product.cost}}</p>
            <a @click="addToCart(product)" class="btn btn-primary">Add to Cart</a>
        </div>
        </div>
    </div>
      
      
      

  </div>
</template>

<script>
export default {
  name: 'Listing',
  props: {
      products:Array,
  },
  data(){
      return {
      }
  },
  methods:{
      addToCart(product){
          this.$emit("addCart",product)
      },
      cartBtnClicked(){
          this.$emit("goToPage","cart")
      }

  }
}
</script>


