<template>
  <button class="btn btn-primary" type="button" disabled>
    <span class="spinner-border spinner-border-sm" role="status" aria-hidden="false"></span>
    Loading...
  </button>
</template>

<script>
export default {
  name: "Loader"
}
</script>

<style scoped>
.btn{
  margin-top: 30px;
  margin-bottom: 20px;
}
</style>