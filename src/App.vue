<template>
  <div id="app">
    <!-- all'evento $emit di startSearch invoco la funzione startSearch -->
    <Head @startSearch="startSearch" />

    <!-- ci sono due componenti Main movie e tv e vengono visualizzati solo se sono presenti nell'aray -->
    <!-- poi li passo due props movie o tv e l'elenco dei risultati -->
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
      // in questo oggetto memmorizo le 2 ricerche
      results: {
        movie: [],
        tv: [],
      },
    };
  },

  methods: {
    // lancio della ricerca
    startSearch(obj) {
      // reset delle ricerce passate
      this.resetResults();
      // se cerca tutto fa due chiamate, le chiamate sono...
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

    // funzione per la chiamata axios
    getAPI(query, type) {
      // e di conseguenza effettua una chiamata solo se c'è un testo da cercare
      if (query !== "") {
        axios
          .get(this.apiUrl + type, {
            params: {
              api_key: this.apiKey,
              query: query,
              language: "it-IT",
            },
          })

          .then((res) => {
            // in base al tipo di ricerca salvo il data nell'array dell'oggetto results
            this.results[type] = res.data.results;
            console.log(this.results);
          })
          .catch((err) => {
            console.log(err);
          });
      }
    },
  },
};
</script>

<style lang="scss">
@import "./assets/style/general.scss";
</style>
