<template>
  <div class="answer">
    <p>
      <strong>Answer: </strong>{{answer.text}}
      <br>
      <strong>Value: </strong>{{answer.value}}
    </p>
  </div>
</template>

<script>
export default {
  name: "Answer",
  props:{
    answer: Object
  }
}
</script>

<style scoped>

</style>