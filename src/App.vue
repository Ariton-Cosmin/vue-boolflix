<template>
  <div id="app">App</div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  components: {},

  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/movie",
      apiKey: "514edf9961ca2d85a642a68d752ce4a9",
    };
  },

  methods: {
    getAPI(query) {
      axios
        .get(this.apiUrl, {
          params: {
            api_Key: this.apiKey,
            query: query,
            language: "it-IT",
          },
        })
        .then((res) => {
          console.log(res.data);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },

  created() {
    this.getAPI("star wars");
  },
};
</script>

<style lang="scss">
@import "./assets/style/general.scss";
</style>
