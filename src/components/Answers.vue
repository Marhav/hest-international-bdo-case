<template>
<div class="answers" :key="answer.questionText" v-for="answer in answers">
  <p><strong>Question: </strong>{{ answer.questionText }}</p>
  <Answer :answer="answer.answer" />
  <hr>
</div>
</template>

<script>
import Answer from "@/components/Answer";

export default {
  name: "Answers",
  props: {
    answers: Array
  },
  components: {
    Answer
  }
}
</script>

<style scoped>
.answers{
  text-align: left;
}
</style>