<template>
  <div class="home">
    <input type="number" v-model="zipcode">
    <button @click="searchAddress">住所自動入力</button>
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
      async searchAddress() {
        const item = await axios.get(
          `https://apis.postcode-jp.com/api/v4`
        )
    }
   }
  }
</script>
