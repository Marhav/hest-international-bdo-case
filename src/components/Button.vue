<template>
  <button type="button" class="btn btn-primary" @click="onClick()">Get New Report</button>
</template>

<script>
export default {
  name: "Button",
  methods: {
    onClick() {
      this.$emit('btn-click')
    }
  }
}
</script>

<style scoped>
.btn{
  margin-top: 30px;
  margin-bottom: 20px;
}
</style>