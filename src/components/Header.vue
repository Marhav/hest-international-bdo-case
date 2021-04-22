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
      <Button @btn-click="$emit('get-report')" />
      <Loader v-show="loading_visible" />
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
    //Below is different check methods used to check if variables has something to display.
    checkIfReport() {
      if (this.survey){
        return true;
      } return false;
    },
    checkName() {
      if (this.survey){
        return this.survey.name;
      } return 'Survey Reports';
    },
    checkLogoImg() {
      if (this.survey){
        return this.survey.logoImage;
      } return '';
    },
    checkDate(){
      if (this.survey){
        return "Expires: " + this.formatDate(this.survey.endDate);
      } return '';
    },
    checkBackground() {
      if (this.survey){
        return this.survey.backgroundImage
      } return '';
    },
    //Formats the date from input and return day and month
    formatDate(input) {

      const date = new Date(input);

      return date.toLocaleDateString('no', {day: 'numeric', month: 'long'})
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