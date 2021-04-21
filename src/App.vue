<template>
  <Header @get-report="getReport" :survey="survey.survey"/>
  <Report :rating="rating" :answers="answers" />
</template>

<script>
const uuid = require('uuid-js')
import axios from "axios"

import Header from "@/components/Header";
import Report from "@/components/Report";

export default {
  name: 'App',
  components: {
    Header,
    Report,
  },
  data() {
    return {
      survey: {},
      answers: {},
      rating: {},
    }
  },
  methods: {
    async getReport() {
      const id = uuid.create();

      const res_survey = await axios.get(`/api/surveys/${id}`);
      this.survey = res_survey.data;

      const res_answers = await axios.get(`/api/surveys/${id}/responses/${id}`);
      this.answers = res_answers.data;

      const res_rating = await axios.get(`/api/surveys/${id}/responses/${id}/scores`);
      this.rating = res_rating.data;
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>


/*
const id = uuid.create();
try{
const res = await axios.get(`https://mango-meadow-01b737303.azurestaticapps.net/api/surveys/${id}`)

this.survey = res.name
} catch (e) {
console.log(e)
}

*/