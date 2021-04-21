<template>
  <header>
    <img class="logoImg" :src="checkLogoImg()" alt="">
    <h1>{{ checkName() }}</h1>
    <h3>{{ checkDate() }}</h3>
    <div>
      <Button @btn-click="$emit('get-report')" /><Loader v-show="loading" />
    </div>
  </header>
</template>

<script>
import Button from "@/components/Button";
import Loader from "@/components/Loader";


export default {
  name: "Header",
  props: {
    survey: Object,
    loading: Boolean,
  },
  components: {
    Button,
    Loader,
  },
  methods: {
    checkName() {
      if (!this.survey){
        return 'Hest International Survey';
      } else return this.survey.name;
    },
    checkLogoImg() {
      if (!this.survey){
        return 'https://i.imgur.com/DiyCbNA.png';
      } else return this.survey.logoImage;
    },
    checkDate(){
      if (!this.survey){
        return '';
      } else return this.formatMonth(this.survey.endDate)
    },
    formatMonth(date) {

      const separated_date = date.split("-");

      const month = separated_date[1];

      if(month == "01"){
        return "January";
      } else if (month == "02"){
        return "February"
      } else if (month == "03"){
        return "March"
      } else if (month == "04"){
        return "April"
      } else if (month == "05"){
        return "May"
      } else if (month == "06"){
        return "June"
      } else if (month == "07"){
        return "July"
      } else if (month == "08"){
        return "August"
      } else if (month == "09"){
        return "September"
      } else if (month == "10"){
        return "October"
      } else if (month == "11"){
        return "November"
      } else if (month == "12"){
        return "December"
      } else {
        console.log("Ugyldig måned: " + separated_date);
      }
    }
  },
}
</script>

<style scoped>
.logoImg{
  width: 15%;
  height: 15%;
}
</style>