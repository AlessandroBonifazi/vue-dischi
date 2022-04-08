<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      // apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
    };
  },
};
</script>

<style lang="scss">
@import "@/style/general";
</style>
