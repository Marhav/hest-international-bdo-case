<template>
  <header class="backgroundImg" :style="{'background-image': `url(${returnBackground()})`}">
    <img class="logoImg" :src="returnLogoImg()" alt="">
    <div class="container">
      <div :class="[checkIfReport() ? 'contrast_background' : '']">
        <h1>{{ returnName() }}</h1>
      </div><br>
      <div :class="[checkIfReport() ? 'contrast_background' : '']">
        <h6>{{ returnDate() }}</h6>
      </div>
    </div>
    <div>
      <Button v-show="!loading_visible" @btn-click="$emit('get-report')" />
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
    returnName() {
      if (this.survey){
        return this.survey.name;
      } return 'Survey Reports';
    },
    returnLogoImg() {
      if (this.survey){
        return this.survey.logoImage;
      } return '';
    },
    returnBackground() {
      if (this.survey){
        return this.survey.backgroundImage
      } return '';
    },
    returnDate(){
      if (this.survey){
        return "Expires: " + this.formatDate(this.survey.endDate);
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
  width: 8%;
  position: absolute;
  top: 15px;
  left: 15px;
}

.backgroundImg{
  background-size: cover;
  background-position: 50% 20%;
  padding-top: 40px;
  padding-bottom: 20px;
}

.contrast_background{
  background-color: #f4f4f4;
  width: fit-content;
  display: inline-block;
  padding-top: 7px;
  padding-right: 15px;
  padding-left: 15px;
  margin-top: 5px;
  margin-left: 15px;
  margin-right: 15px;
  border-radius: 3px;
}

.container{
  text-align: center;
}
</style>