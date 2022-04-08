<template>
  <main>
    <div v-if="albums.length === 10" class="main">
      <!-- card -->
      <div v-for="(item, index) in albums" :key="index" class="ab-card">
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

export default {
  name: "AlbumList",
  data() {
    return {
      albums: [],
    };
  },
  props: {
    url: String,
  },
  components: {
    Loader,
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
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/variables";

.main {
  margin: 50px auto;
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