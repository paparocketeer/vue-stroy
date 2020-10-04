<template>
  <div id="app">
    <TopBar />
    <Header />
  </div>
</template>

<script>
import TopBar from "./components/TopBar.vue";
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: {
    TopBar,
    Header
  }
};
</script>

<style lang="scss">
@import "assets/scss/main";
</style>
