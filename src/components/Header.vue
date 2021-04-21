<template>
  <header>
    <img class="logoImg" :src="survey.logoImage" alt="">
    <h1>{{ survey.name }}</h1>
    <h3>{{ survey.endDate }}</h3>
    <Button @btn-click="$emit('get-report')" />
  </header>
</template>

<script>
import Button from "@/components/Button";


export default {
  name: "Header",
  props: {
    survey: Object
  },
  components: {
    Button
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