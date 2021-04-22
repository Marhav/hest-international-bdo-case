<template>
  <div class="report">
    <p><strong>Results:</strong> {{ rating.score }}, {{ rating.rating }} {{getEmoji()}}</p>
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
  methods: {
    //Get an emoji based on rating
    getEmoji() {
      if (!this.rating.score) {
        return '';
      }

      if (this.rating.score > 4){
        return '🤗';
      }
      if (this.rating.score > 3){
        return '😏';
      }
      if (this.rating.score > 2){
        return '🤔';
      }
      if (this.rating.score > 1){
        return '😢';
      }
      return '😭';

    }
  }
}
</script>

<style scoped>
.report{
  background: #f4f4f4;
  margin-top: 5px;
  margin-bottom: 5px;
  padding: 10px 20px;
  border-radius: 10px;
}
</style>