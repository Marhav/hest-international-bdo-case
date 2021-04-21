<template>
  <div class="report">
    <p><strong>Results:</strong> {{ report.score }}, {{ report.rating }}</p>
    <p></p>
    <p></p>
    <h2>Answers:</h2>
    <Answers :answers="report.answers" />
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
    report: Object
  },
}
</script>

<style scoped>
.report{
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  border-radius: 10px;
}
</style>