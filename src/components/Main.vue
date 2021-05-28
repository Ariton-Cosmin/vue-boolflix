<template>
  <main class="container">
    <h2>{{ titles[type] }}</h2>
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
        movie: "film trovati",
        tv: "serie tv trovati",
      },
    };
  },
};
</script>

<style lang="scss" scoped>
main {
  width: 85%;
  margin: auto;

  h2 {
    color: red;
  }
}
</style>