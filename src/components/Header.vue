<template>
  <div class="container-fluid">
    <div class="row">
      <div class="header col-12 d-flex align-items-center">
        <img src="../assets/spotify-logo.png" alt="spotify logo" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",
};
</script>

<style lang="scss" scoped>
@import "@/style/variables";
.header {
  background-color: $bg-secondary;
  height: 70px;
  img {
    height: 50px;
  }
}
</style>