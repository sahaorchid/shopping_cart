<template>
    <div>
    <Listing v-if="currentPage=='listing'" :cart="totalItem" :products="products"  @addCart="addToCart($event)" @goToPage="goToPage($event)" @click="total"/>
    <Cart  v-if="currentPage=='cart'" :cart="cart" @goToPage="goToPage($event)" :Total="subTotal"/>
    </div>
</template>

<script>
import Listing from './components/Listing.vue'
import Cart from './components/Cart.vue'

export default {
  name: 'App',
  components: {
    Listing,
    Cart
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
      cart:[],
      id:0,
      totalItem:0,
      subTotal:0,
    }
  },
  methods:{
    addToCart(product){
      let item=(this.cart.find((item)=>{
       return  item.product_name==product.product_name
        }))
      if(item){
        this.totalItem+=1
        item.qty+=1
      }
      else{
        this.id+=1
        this.totalItem+=1
        this.cart.push({id:this.id,product_name:product.product_name,cost:product.cost,qty:1,currency_sign:product.currency_sign})
      }
    },
    goToPage(value){
      this.currentPage = value
    },
    total(){
      this.subTotal=this.cart.reduce((total,item)=>{
        return total+=(item.cost*item.qty)
      },0)

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
