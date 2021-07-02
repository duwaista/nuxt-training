<template>
  <div class="boobas-container">
    <h1 class="boobas"><span>No boobas</span></h1>
    <span><nuxt-link to="/boobas">Go to boobas</nuxt-link></span>
  </div>
</template>

<script lang="js">
import Vue from 'vue'

export default Vue.extend({})
</script>
<style scoped>
.boobas-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100vh;
}
@media (prefers-color-scheme: light) {
  .boobas-container {
    background-color: white;
  }
}
@media (prefers-color-scheme: dark) {
  .boobas-container {
    background-color: black;
  }
}
</style>

