<template>
  <div class="container">
    <div class="report">
      <p><strong>Results:</strong> {{ rating.score }}, {{ rating.rating }} {{getEmoji()}}</p>
      <h2>Answers:</h2>
      <hr>
      <Answers :answers="answers" />
    </div>
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
    answers: Array,
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
.container{
  text-align: center;
}
.report{
  background: #f4f4f4;
  margin: 10px;
  padding: 10px 20px;
  border-radius: 10px;
  max-width: 1000px;
  display: inline-block;
}
</style>