<template>
  <div id="app">
    <Head @startSearch="startSearch" />

    <Main v-if="results.movie.length > 0" type="movie" :list="results.movie" />
    <Main v-if="results.tv.length > 0" type="tv" :list="results.tv" />
  </div>
</template>

<script>
import axios from "axios";
import Head from "./components/Head.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Head,
    Main,
  },

  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "514edf9961ca2d85a642a68d752ce4a9",
      results: {
        movie: [],
        tv: [],
      },
    };
  },

  methods: {
    startSearch(obj) {
      this.resetResults();
      if (obj.type === "all") {
        this.getAPI(obj.text, "movie");
        this.getAPI(obj.text, "tv");
      } else {
        this.getAPI(obj.text, obj.type);
      }
    },

    resetResults() {
      this.results.movie = [];
      this.results.tv = [];
    },

    getAPI(query, type) {
      axios
        .get(this.apiUrl + type, {
          params: {
            api_key: this.apiKey,
            query: query,
            language: "it-IT",
          },
        })
        .then((res) => {
          this.results[type] = res.data.results;
          console.log(this.results);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },

  created() {},
};
</script>

<style lang="scss">
@import "./assets/style/general.scss";
</style>
