<template>
  <div class="home">
    <input type="number" v-model="postcode">
    <button @click="getAddress">住所自動入力</button>
    <p>Address: {{address}}</p>
   
  </div>
</template>

<script>
import axios from "axios";
  export default {
    data() {
      return {
        postcode:"",
        address:""
      }
    },
    methods: {
      async getAddress() {
        const item = await axios.get(
         `https://apis.postcode-jp.com/api/v4/postcodes?postcode=${this.address}&nT5ps9J9PuqhczFKUcBP9ODlYd9HfbVbEtOhaHx`
        );
        const addressData = item.data;
        this.address = addressData.address
     }
   }
  }
</script>
