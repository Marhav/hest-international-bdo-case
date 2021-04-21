<template>
  <header>
    <img class="logoImg" :src="survey.logoImage" alt="">
    <h1>{{ survey.name }}</h1>
    <h3>{{ survey.endDate }}</h3>
  </header>
</template>

<script>
//const uuid = require('uuid-js')
//import axios from "axios"


export default {
  name: "Header",
  props: {
    survey: Object
  },
  methods: {

  },
}
</script>

<style scoped>
.logoImg{
  width: 15%;
  height: 15%;
}

</style>