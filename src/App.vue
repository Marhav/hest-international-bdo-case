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
      survey: Object,
      answers: {},
      rating: Object
    }
  },
  methods: {
    async getReport() {
      console.log('click')
      const id = uuid.create()

      console.log(`https://mango-meadow-01b737303.azurestaticapps.net/api/surveys/${id}`)

      this.survey = await axios.get(`https://mango-meadow-01b737303.azurestaticapps.net/api/surveys/${id}`)
    }
  },
  async created() {

    this.survey = {
      "survey": {
        "name": "Hest International Survey",
        "slug": "hest-international-survey",
        "surveyKey": "b113502f-6eba-40fe-83fc-d7dd65bfdb33",
        "customerKey": "hest-international-b113502f-6eba-40fe-83fc-d7dd65bfdb33",
        "description": "The future of horse racing is here! The dawn of new and interesting advances in technology allows for even more engaging content to our users. Through this survey, you'll help us understand how to better cater to a broader audience.",
        "logoImage": "https://i.imgur.com/DiyCbNA.png",
        "backgroundImage": "https://imgur.com/vJxazQI.jpg",
        "startDate": "2021-03-21T11:47:40.630Z",
        "endDate": "2021-05-21T11:47:40.630Z",
        "anonymous": true
      }
    }


    this.rating = {
      "score": "2.71",
      "rating": "Passable"
    }

    this.answers = {
      "answers": [
        {
          "questionText": "Horse Racing is important for my day",
          "answer": {
            "text": "Agree",
            "value": 4
          }
        },
        {
          "questionText": "Could tournaments be arranged more locally?",
          "answer": {
            "text": "Agree",
            "value": 4
          }
        },
        {
          "questionText": "On a scale from 1 to 5, how likely would you be to recommend Horse Racing tournaments to your friends?",
          "answer": {
            "text": "To some extent",
            "value": 2
          }
        },
        {
          "questionText": "Adding more new types of events would benefit local participation",
          "answer": {
            "text": "No",
            "value": 0
          }
        },
        {
          "questionText": "Have you won any bets on Horse Racing lately?",
          "answer": {
            "text": "Agree",
            "value": 4
          }
        },
        {
          "questionText": "Prioritizing home work before spare time activities is important",
          "answer": {
            "text": "Totally disagree",
            "value": 1
          }
        },
        {
          "questionText": "How has the internet affected your work?",
          "answer": {
            "text": "Somewhat agree",
            "value": 3
          }
        },
        {
          "questionText": "Would you like to see more providers offer Horse Racing Streams?",
          "answer": {
            "text": "Like today",
            "value": 5
          }
        },
        {
          "questionText": "Have you heard about Hest International?",
          "answer": {
            "text": "It is a vital part of my day",
            "value": 5
          }
        },
        {
          "questionText": "Training every day is important for both physical and mental health",
          "answer": {
            "text": "Totally disagree",
            "value": 1
          }
        },
        {
          "questionText": "Have you watched any tournaments in the last month?",
          "answer": {
            "text": "It is a vital part of my day",
            "value": 5
          }
        },
        {
          "questionText": "I think more countries should be allowed to participate in Horse Racing Tournaments",
          "answer": {
            "text": "I am considering",
            "value": 2
          }
        },
        {
          "questionText": "Will people look for entertainment online more than they do today?",
          "answer": {
            "text": "Agree",
            "value": 4
          }
        },
        {
          "questionText": "Who is your favorite racer this season?",
          "answer": {
            "text": "It is a vital part of my day",
            "value": 5
          }
        }]
    }
  }
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