<template>
  <header>
    <img src="../assets/spotify-logo.png" alt="spotify logo" />
  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
};
</script>

<style lang="scss" scoped>
@import "@/style/variables";

header {
  display: flex;
  align-items: center;
  background-color: $bg-secondary;
  height: 70px;
  img {
    height: 50px;
    margin-left: 30px;
  }
}
</style>