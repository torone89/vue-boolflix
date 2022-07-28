<template>
  <div id="app">
    <base-header />
    <the-main />
  </div>
</template>

<script>
import BaseHeader from "./components/BaseHeader.vue";
import TheMain from "./components/TheMain.vue";
// Import Sass
import "./assets/sass/style.scss";
export default {
  name: "App",
  components: {
    BaseHeader,
    TheMain,
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
