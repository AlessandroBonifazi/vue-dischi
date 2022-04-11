<template>
  <div>
    <select @change="setGenreValue($event)">
      <option value="All">All</option>
      <option value="Rock">Rock</option>
      <option value="Metal">Metal</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "SearchComponent",
  data() {
    return {
      selectedGenre: "",
    };
  },
  methods: {
    setGenreValue(event) {
      console.log(event.target.value);
      this.selectedGenre = event.target.value;
      this.$emit("filterByGenre", this.selectedGenre);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>