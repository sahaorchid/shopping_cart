<template>
  <div>
     <h1>{{cart}}</h1>
     <h2>{{user_data}}</h2>
     <h1>product info</h1>

  </div>
</template>

<script>
//confetti 
// const confetti = require('canvas-confetti');
// var myCanvas = document.createElement('canvas');
// document.body.appendChild(myCanvas);

// var myConfetti = confetti.create(myCanvas, {
//   resize: true,
//   useWorker: true
// });
// myConfetti({
//   particleCount: 100,
//   spread: 160
// });
export default {
  name: 'Success',
  props: {
      cart:Array,
      user_data:Array
  },
  data(){
      return {
          name:null,
          email:null,
          address:null
          
      }
  },
  created:function(){
      const confetti = require('canvas-confetti');
var myCanvas = document.createElement('canvas');
document.body.appendChild(myCanvas);

var myConfetti = confetti.create(myCanvas, {
  resize: true,
  useWorker: true
});
myConfetti({
  particleCount: 100,
  spread: 160
});

  },
  methods:{
      dataSubmit(e){
          e.preventDefault();
          alert(`Name:${this.name},Email:${this.email},Address:${this.address}`)
      }


  },
  
}
</script>
<style>

</style>


