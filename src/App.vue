<style lang="scss">
@import "@/style/DarckMod.scss";
</style>
<template>
  <div id="app">
    <TranslationPage />
  </div>
</template>

<script>
import TranslationPage from "./components/TranslationPage.vue";

export default {
  name: "app",
  components: {
    TranslationPage
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
}
</style>
