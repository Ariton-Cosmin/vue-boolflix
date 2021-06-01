<template>
  <main class="container">
    <!-- mostro a video il titolo relativo al tipe -->
    <h2>{{ titles[type] }}</h2>

    <!-- ciclo la lista dei risultati in Card -->
    <Card v-for="card in list" :key="card.id" :card="card" />
  </main>
</template>

<script>
import Card from "../components/Card.vue";

export default {
  name: "Main",
  components: {
    Card,
  },

  props: {
    type: String,
    list: Array,
  },

  data() {
    return {
      titles: {
        movie: "Film trovati",
        tv: "Serie tv trovati",
      },
    };
  },
};
</script>

<style lang="scss" scoped>
main {
  padding-top: 70px;
  width: 85%;
  margin: auto;

  h2 {
    color: red;
  }
}
</style>