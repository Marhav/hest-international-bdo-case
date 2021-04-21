<template>
  <div class="lds-dual-ring"></div>
</template>

<script>
export default {
  name: "Loader"
}
</script>

<style scoped>
.lds-dual-ring {
  display: inline-block;
  width: 28px;
  height: 28px;
}
.lds-dual-ring:after {
  content: " ";
  display: block;
  width: 16px;
  height: 16px;
  margin: 8px;
  border-radius: 50%;
  border: 6px solid #261051;
  border-color: #261051 transparent #261051 transparent;
  animation: lds-dual-ring 1.2s linear infinite;
}
@keyframes lds-dual-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>