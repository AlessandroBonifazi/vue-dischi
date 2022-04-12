<template>
  <div class="select-container">
    <select @change="setGenreValue($event)" class="ab-select">
      <option value="All">All Genres</option>
      <option value="Rock">Rock</option>
      <option value="Metal">Metal</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
    </select>

    <select @change="setArtistValue($event)" class="ab-select">
      <option value="All">All Artists</option>
      <option value="Bon Jovi">Bon Jovi</option>
      <option value="Queen">Queen</option>
      <option value="Sting">Sting</option>
      <option value="Steve Gadd Band">Steve Gadd Band</option>
      <option value="Iron Maiden">Iron Maiden</option>
      <option value="Eric Clapton">Eric Clapton</option>
      <option value="Deep Purple">Deep Purple</option>
      <option value="Metallica">Metallica</option>
      <option value="Dave Weckl">Dave Weckl</option>
      <option value="Michael Jacjson">Michael Jacjson</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "SearchComponent",
  data() {
    return {
      selectedGenre: "",
      selectedArtist: "",
    };
  },
  methods: {
    setGenreValue(event) {
      console.log(event.target.value);
      this.selectedGenre = event.target.value;
      this.$emit("emitGenre", this.selectedGenre);
    },
    setArtistValue(event) {
      this.selectedArtist = event.target.value;
      console.log(event.target.value);
      this.$emit("emitArtist", this.selectedArtist);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/variables";

.select-container {
  margin-top: 20px;
  .ab-select {
    height: 35px;
    margin: 5px;
    padding: 5px;
    border: 2px solid rgba(255, 255, 255, 0.678);
    border-radius: 10px;
    color: white;
    background-color: $bg-secondary;
  }
}
</style>