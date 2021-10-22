<template>
  <div class="success-main">
    <div class="success-img">
      <SuccessImg />
    </div>
    <div class="success-info" style="font-size:30px;">
      {{text}}
    </div>
    <p class="hi" style="font-size:30px;">Name: {{name}}</p>
    <p class="hi" style="font-size:30px;">Address: {{address}}</p>
    <p style="font-size:30px;">{{text1}}</p>
  </div>
</template>

<script>
//import { mapGetters } from "vuex";
import SuccessImg from "../success/SuccessImg.vue";
export default {
name:"checkout",

data(){
    // var name=localStorage.getItem('name');
    // console.log(name);
    return{
        text: "ORDER PLACED SUCCESSFULLY",
        name: localStorage.getItem('name'),
        address: localStorage.getItem('address'),
        text1: "Thank You!!"

    };
    
},
components: {
    SuccessImg,
  },
}
</script>

<style>

</style>
