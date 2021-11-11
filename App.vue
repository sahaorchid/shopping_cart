<template>
    <div>
      <Listing v-if="currentPage=='listing'" :cart="totalItem" :products="products"  @addCart="addToCart($event)" @goToPage="goToPage($event)" @click="total"/>
      <Cart  v-if="currentPage=='cart'" :cart="cart" @goToPage="goToPage($event)" :Total="subTotal"/>
      <Checkout v-if="currentPage=='checkout'" @goToPage="goToPage($event)" @userData="userData($event)"/>
      <Success v-if="currentPage=='success'"  @goToPage="goToPage($event)" :cart="cart"  :user_data="user_data"/>
    </div>
</template>

<script>
import Listing from './components/Listing.vue'
import Cart from './components/Cart.vue'
import Checkout from './components/Checkout.vue'
import Success from './components/Success.vue'

export default {
  name: 'App',
  components: {
    Listing,
    Cart,
    Checkout,
    Success
  },
  data(){
    return {
      currentPage:"listing",
      products:[
        {
          product_name: 'Laptop',
          cost: 450,
          currency_sign: '$',
        },
        {
          product_name: 'Mobiles',
          cost: 300,
          currency_sign: '$',
        },
        {
          product_name: 'Desktops',
          cost: 800,
          currency_sign: '$',
        },
      ],
      cart: [],
      id: 0,
      totalItem: 0,
      subTotal: 0,
      user_data: {}
    }
  },
  methods:{
    addToCart(product){
      let item = (this.cart.find((item)=>{
       return  item.product_name == product.product_name
        }))
      if(item){
        this.totalItem+= 1
        item.qty+= 1
      }
      else{
        this.id+= 1
        this.totalItem+= 1
        this.cart.push({...product,id:this.id,qty:1})
      }
    },
    goToPage(value){
      this.currentPage = value
    },
    total(){
      this.subTotal=this.cart.reduce((total,item)=>{
        return total+= (item.cost*item.qty)
      },0)
    },
    userData(data){
      this.user_data = (data)
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
  margin-top: 60px;
}
</style>
