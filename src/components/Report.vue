<template>
  <div class="report">
    <p><strong>Results:</strong> {{ rating.score }}, {{ rating.rating }}</p>
    <h2>Answers:</h2>
    <Answers :answers="answers.answers" />
  </div>
</template>

<script>
import Answers from "@/components/Answers";

export default {
  name: "Report",
  components: {
    Answers
  },
  props: {
    rating: Object,
    answers: {},
  },
}
</script>

<style scoped>
.report{
  background: #f4f4f4;
  margin: 5px;
  margin-top: 30px;
  padding: 10px 20px;
  border-radius: 10px;
}
</style>