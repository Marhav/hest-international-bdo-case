<template>
  <header class="backgroundImg" :style="{'background-image': `url(${getBackground()})`}">
    <img class="logoImg" :src="getLogoImg()" alt="">
    <div class="container">
      <div :class="[checkIfReport() ? 'contrast_background' : '']">
        <h1>{{ getName() }}</h1>
      </div><br>
      <div :class="[checkIfReport() ? 'contrast_background' : '']">
        <h6>{{ getDate() }}</h6>
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
    //Below is methods used to check whether variables has something to display or not.
    checkIfReport() {
      if (this.survey){
        return true;
      } return false;
    },
    getName() {
      if (this.survey){
        return this.survey.name;
      } return 'Survey Reports';
    },
    getLogoImg() {
      if (this.survey){
        return this.survey.logoImage;
      } return '';
    },
    getBackground() {
      if (this.survey){
        return this.survey.backgroundImage
      } return '';
    },
    getDate(){
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