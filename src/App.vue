<template>
  <div id="app">
    <Home :v-for="(disc, index) in discs" :key="disc" :disc="disc" />
  </div>
</template>

<script>
import axios from "axios";
import Home from "./components/Home.vue";

export default {
  name: "App",
  components: {
    Home,
  },

  data() {
    return {
      axios,
      discs: [],
    };
  },

  created() {
    axios
      .get(
        "https://api.themoviedb.org/3/search/movie?api_key=514edf9961ca2d85a642a68d752ce4a9&query=ritorno al futuro&language=it-IT"
      )
      .then((response) => {
        this.discs = response.data.response;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style lang="scss">
</style>
