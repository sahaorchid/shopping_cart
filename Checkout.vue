<template>
  <div>
<form class="row g-3" @submit="dataSubmit">
  <div class="col-md-6">
    <label for="inputEmail4" class="form-label">Name</label>
    <input type="text" class="form-control" id="inputEmail4" name="name" v-model="name">
  </div>
  <div class="col-md-6">
    <label for="inputPassword4" class="form-label">Email</label>
    <input type="Email" class="form-control" id="inputPassword4" name="email" v-model="email">
  </div>
  <div class="col-12">
    <label for="inputAddress" class="form-label">Address</label>
    <input type="text" class="form-control" id="inputAddress" name="address" v-model="address" >
  </div>
  <div class="col-12">
    <button type="submit" class="btn btn-primary" >Place Order</button>
  </div>
</form>    
  </div>
</template>

<script>
export default {
  name: 'Checkout',

  props: {
  },
  data(){
      return {
          name: null,
          email: null,
          address: null,
          value: false      
      }
  },
  methods:{
      dataSubmit(e){
          e.preventDefault();
          alert(`Name:${this.name},Email:${this.email},Address:${this.address}`)
          this.$emit("goToPage","success")
          this.$emit("userData",{Name:this.name,Email:this.email,Address:this.address})
      }
  },  
}
</script>



