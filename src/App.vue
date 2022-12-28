<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header class="container mx-auto mb-6">
    <img alt="Vue logo" class="logo mb-4" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper mx-auto">
      <HelloWorld msg="Welcome to vue api project" />
    </div>
  </header>



<div  class="countries-container justify-center container mx-auto  gap-10">
  <div  v-for="country in countries"  class="border px-4  mt-10">
    <div class="border border-gray-200 mb-4 h-auto ">
            <h2>Name: {{ country.name.common }}</h2>
           <img :src="country.flags.png" alt="" />
          <p>Area: {{ country.name.area }}</p>
          <p><small>Region: {{country.region}}</small></p>
    </div>
  </div>
</div>

</template>

<script>
  export default {
    data() {
      return {
        countries: []
      }
    },
    methods: {
      async getData() {
        const res = await fetch("https://restcountries.com/v3.1/all");
        const finalRes = await res.json();
        this.countries = finalRes;
      }
    },
    mounted() {
      this.getData()
    }
  }
</script>
<style scoped>

</style>
