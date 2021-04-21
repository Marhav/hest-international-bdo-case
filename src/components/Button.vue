<template>
  <button @click="onClick()">Get Report</button>
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
button {
  display: inline-block;
  background: #261051;
  color: #fff;
  border: none;
  padding: 10px 15px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
}
</style>