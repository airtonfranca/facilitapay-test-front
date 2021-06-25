<template>
  <div id="app">
    <Header />
    <router-view />
  </div>
</template>
<script lang="ts">
import Vue from "vue";
import Header from "./components/Header.vue";
export default Vue.extend({
  components: {
    Header
  }
});
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
}

body {
  background: rgb(2, 0, 36);
  background: linear-gradient(
    90deg,
    rgba(2, 0, 36, 1) 0%,
    rgba(16, 18, 105, 1) 30%,
    rgba(4, 142, 162, 1) 80%,
    rgba(0, 255, 197, 1) 100%
  );
  background-size: cover;
}
</style>
