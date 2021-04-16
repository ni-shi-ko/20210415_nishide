<template>
  <div class="home">
    <input type="number" v-model="zipcode">
    <button @click="gethAddress">住所自動入力</button>
    <p>Address: {{address}}</p>
   
  </div>
</template>

<script>
import axios from "axios";
  export default {
    data() {
      return {
        zipcode:"",
        address:""
      }
    },
    methods: {
      async getAddress() {
        const item = await axios.get(
          `https://apis.postcode-jp.com/api/v4/postcodes`
        );
        console.log(item);
    }
   }
  }
</script>
