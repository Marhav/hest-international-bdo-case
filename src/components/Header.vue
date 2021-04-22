<template>
  <header class="backgroundImg" :style="{'background-image': `url(${checkBackground()})`}">
    <img class="logoImg" :src="checkLogoImg()" alt="">
    <div class="container">
      <div :class="[checkIfReport() ? 'contrast_background' : '']">
        <h1>{{ checkName() }}</h1>
      </div><br>
      <div :class="[checkIfReport() ? 'contrast_background' : '']">
        <h3>{{ checkDate() }}</h3>
      </div>
    </div>
    <div>
      <Button @btn-click="$emit('get-report')" /><Loader v-show="loading_visible" />
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
    loading_visible: Boolean,
  },
  components: {
    Button,
    Loader,
  },
  methods: {
    checkIfReport() {
      if (this.survey){
        return true;
      } else return false;
    },
    checkName() {
      if (!this.survey){
        return 'Survey Reports';
      } else return this.survey.name;
    },
    checkLogoImg() {
      if (!this.survey){
        return '';
      } else return this.survey.logoImage;
    },
    checkDate(){
      if (!this.survey){
        return '';
      } else return "Expires: " + this.formatDate(this.survey.endDate)
    },
    checkBackground() {
      if (this.survey){
        return this.survey.backgroundImage
      } else return '';
    },
    formatDate(date) {

      const separated_date = date.split(/([-,T,])/);

      const month = separated_date[2];
      const day = separated_date[4]

      if(month == "01"){
        return day + ". January";
      } else if (month == "02"){
        return day + ". February"
      } else if (month == "03"){
        return day + ". March"
      } else if (month == "04"){
        return day + ". April"
      } else if (month == "05"){
        return day + ". May"
      } else if (month == "06"){
        return day + ". June"
      } else if (month == "07"){
        return day + ". July"
      } else if (month == "08"){
        return day + ". August"
      } else if (month == "09"){
        return day + ". September"
      } else if (month == "10"){
        return day + ". October"
      } else if (month == "11"){
        return day + ". November"
      } else if (month == "12"){
        return day + ". December"
      } else {
        console.error("Ugyldig måned: " + separated_date);
      }
    },
  },
}
</script>

<style scoped>
.logoImg{
  width: 10%;
  position: absolute;
  top: 20px;
  left: 20px;
}

.backgroundImg{
  background-size: cover;
  padding-top: 60px;
  padding-bottom: 20px;
  border-radius: 10px;
}

.contrast_background{
  background: rgba(0, 0, 0, 0.7);
  color: azure;
  width: fit-content;
  display: inline-block;
  padding-right: 5px;
  padding-left: 5px;
  margin-bottom: 15px;
  border-radius: 3px;
}

.container{
  text-align: center;
}
</style>