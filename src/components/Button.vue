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

</style>