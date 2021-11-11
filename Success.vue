<template>
  <div id="div">
     <h1>product info</h1>
     <div v-for="product in cart" :key="product.product_name">
        <p scope="row">{{product.product_name}}</p>
        <p>{{product.currency_sign}}{{product.cost}}</p>
        <p>{{product.qty}}x</p>
        <p id="name">{{product.cost*product.qty}}</p>
     </div>
     <h1>User Details</h1>
     <p>{{user_data.Name}}</p>
     <p>{{user_data.Email}}</p>
     <p>{{user_data.Address}}</p>
  </div>
</template>

<script>
import confetti from 'canvas-confetti'
let myCanvas = document.createElement('canvas');
export default {
  name: 'Success',
  props: {
      cart: Array,
      user_data: Object
  },
  data(){
      return {
          name: null,
          email: null,
          address: null   
      }
  },
  created:function(){
    if(myCanvas){
        let canvas=document.getElementById("canvas")
        let myConfetti = confetti.create(canvas, {
        resize: true,
        useWorker: true
        });
        myConfetti({
        particleCount: 100,
        spread: 10
        });
    }
    else{
        myCanvas.setAttribute('id','canvas')
        document.body.appendChild(myCanvas);
    }
  },
  methods:{
      dataSubmit(e){
          e.preventDefault();
          alert(`Name:${this.name},Email:${this.email},Address:${this.address}`)
      }
  },  
}
</script>



