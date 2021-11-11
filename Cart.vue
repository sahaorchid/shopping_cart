<template>
  <div >
    
    
    
    <div class="d-grid gap-4">
            <button class="btn btn-primary" type="button" @click="productBtnClicked">Go To Products</button>
    </div>
        <div class="d-grid gap-4">
            <button class="btn btn-primary" type="button" @click="checkoutBtn">Checkout</button>
    </div>
    <h1 v-if="cart.length==0" class="container">No Items in Cart</h1>

<!-- table -->
<div v-else>

    <table class="table table-striped table-hover">
    <thead>
        <tr>
        <th scope="col">Name</th>
        <th scope="col">Price</th>
        <th scope="col">Quantity</th>
        <th scope="col">Sub total</th>
        </tr>
    </thead>
    <tbody v-for="product in cart" :key="product.product_name" >
        <tr>
        <th scope="row">{{product.product_name}}</th>
        <td>{{product.currency_sign}}{{product.cost}}</td>
        <td>{{product.qty}}x</td>
        <td>{{product.cost*product.qty}}</td>
        </tr>
        
    </tbody>
    </table>
    <h1 >SubTotal:{{subTotal}}</h1>
</div>
      
      
      

  </div>
</template>

<script>
export default {
  name: 'Cart',
  props: {
      cart:Array,
      Total:String
  },
  data(){
      return {
          subTotal:0
          
      }
  },
  methods:{
      productBtnClicked(){
          this.$emit("goToPage","listing")
      },
      checkoutBtn(){
          this.$emit("goToPage","checkout")
      }


  },
created:function(){
    this.subTotal=this.cart.reduce((total,item)=>{
            return total+=(item.cost*item.qty)
      },0)
    }
  
}
</script>
<style>

</style>


