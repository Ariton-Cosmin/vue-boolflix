<template>
  <div></div>
</template>

<script>
export default {
  name: "Home",
  props: {
    home: Object,
  },

  data() {
    return {
      apiURL: "https://api.themoviedb.org/3/search/movie",
      apiKey: "514edf9961ca2d85a642a68d752ce4a9",
      query: "ritorno al futuro",
    };
  },

  created() {
    axis
      .get(this.apiURL, {
        params: {
          api_key: this.apiKey,
          query: this.query,
          language: "it-IT",
        },
      })
      .then((resp) => {
        console.log(resp.data);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style lang="scss" scoped>
</style>