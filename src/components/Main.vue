<template>
  <main>
    <!-- search -->
    <SearchComponent @emitArtist="filterByArtist" @emitGenre="filterByGenre" />
    <div v-if="!loading" class="ab-container">
      <!-- card -->
      <div v-for="(item, index) in filteredAlbums" :key="index" class="ab-card">
        <!-- img -->
        <img :src="item.poster" :alt="item.title" />
        <!-- details -->
        <h2>{{ item.title }}</h2>
        <h5>{{ item.author }}</h5>
        <h5>{{ item.year }}</h5>
      </div>
    </div>
    <div v-else>
      <Loader />
    </div>
  </main>
</template>

<script>
import axios from "axios";
import Loader from "../components/Loader.vue";
import SearchComponent from "../components/SearchComponent.vue";

export default {
  name: "AlbumList",
  data() {
    return {
      albums: [],
      genre: "",
      artist: "",
    };
  },
  props: {
    url: String,
  },
  computed: {
    loading() {
      return this.albums.lenght === 0;
    },
    filteredAlbums() {
      const filteredByGenre =
        this.genre.lenght === 0 || this.genre === "All"
          ? this.albums
          : this.albums.filter((item) =>
              item.genre.toLowerCase().includes(this.genre.toLowerCase())
            );

      if (this.artist.lenght === 0 || this.artist === "All") {
        return filteredByGenre;
      }
      return filteredByGenre.filter((item) =>
        item.author.toLowerCase().includes(this.artist.toLowerCase())
      );
    },
  },
  components: {
    Loader,
    SearchComponent,
  },
  mounted() {
    this.loadData();
  },

  methods: {
    loadData() {
      axios
        .get(this.url)
        .then((response) => {
          if (response.status === 200) {
            this.albums = response.data.response;
            console.log(this.albums);
          }
        })
        .catch((error) => {
          console.log(error);
        });
    },
    filterByGenre(genre) {
      this.genre = genre;
    },
    filterByArtist(artist) {
      this.artist = artist;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/variables";
main {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.ab-container {
  margin: 30px auto;
  max-width: 1000px;
  display: flex;
  flex-wrap: wrap;
  .ab-card {
    width: 180px;
    margin: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: $bg-secondary;
    padding-top: 15px;
    border-radius: 5px;
    h2 {
      font-size: 20px;
      font-weight: $bold;
      margin-top: 15px;
      text-transform: uppercase;
    }
    h5 {
      font-size: 15px;
      color: grey;
    }
    img {
      height: 150px;
      width: 150px;
    }
  }
}
</style>