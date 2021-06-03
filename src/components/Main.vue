<template>
  <main>
    <!-- mostro a video il titolo relativo al tipe -->
    <h2>{{ titles[type] }}</h2>

    <div class="flex">
      <!-- ciclo la lista dei risultati in Card -->
      <Card v-for="card in list" :key="card.id" :card="card" />
    </div>
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
    // qua viene memmorizato il tipo di risultato
    type: String,
    // qua viene memmorizato l'elenco
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
  width: 87%;
  margin: auto;

  h2 {
    color: red;
  }

  .flex {
    display: flex;
    width: 100%;
    flex-wrap: wrap;
  }
}
</style>