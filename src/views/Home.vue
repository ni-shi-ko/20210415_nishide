<template>
  <div class="home">
    <div class="address-wrap">
      <div class="address">
        <input type="text" v-model="postcode">
        <button @click="getAddress">住所自動入力</button>
      </div>
        <p>Address: {{address}}</p>
    </div>
   
  </div>
</template>

<script>
import axios from "axios";
  export default {
    data() {
      return {
        postcode:"",
        address:""
      };
    },
    methods: {
      async getAddress() {
        const item = await axios.get(
         `https://apis.postcode-jp.com/api/v4/postcodes/${this.postcode}?apiKey=nT5ps9J9PuqhczFKUcBP9ODlYd9HfbVbEtOhaHx `
        );
         console.log(item.data[0].allAddress);
        const Address = item.data;
        this.address = Address[0].allAddress
     }
   }
  }
</script>

<style>
.address-wrap {
  margin-left: 10px;
}
.address {
  margin: 10px 0 20px;
}

</style>
