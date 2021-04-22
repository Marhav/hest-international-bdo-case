<template>
<div class="answers" :key="answer.questionText" v-for="answer in answers">
  <p><strong>Question: </strong>{{ answer.questionText }}</p>
  <Answer :answer="answer.answer" />
  <br>
</div>
</template>

<script>
import Answer from "@/components/Answer";

export default {
  name: "Answers",
  props: {
    answers: {}
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