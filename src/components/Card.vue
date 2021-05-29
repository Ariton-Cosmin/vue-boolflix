<template>
  <div>
    <ul>
      <li><span>Title:</span> {{ card.title || card.name }}</li>
      <li>
        <span>Original name:</span>
        {{ card.original_title || card.original_name }}
      </li>

      <li v-if="flags.includes(card.original_language)">
        <img
          :src="require(`../assets/img/${card.original_language}.png`)"
          :alt="card.original_language"
        />
      </li>

      <li v-else><span>Langauge:</span> {{ card.original_language }}</li>
      <li><span>Langauge:</span> {{ card.original_language }}</li>
      <li><span>Vote:</span> {{ card.vote_average }}</li>
      <li class="overview"><span>overview:</span> {{ card.overview }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    card: Object,
  },

  data() {
    return {
      flags: ["it", "en"],
    };
  },
};
</script>

<style lang="scss" scoped>
div {
  width: 80%;
  padding: 1rem;

  ul {
    border-radius: 10px;
    overflow: hidden;
    background-color: white;

    li {
      line-height: 30px;
      padding-left: 5px;
      list-style: none;
      border: 1px solid rgba(0, 0, 0, 0.3);

      span {
        color: gray;
      }

      img {
        width: 40px;
        padding-top: 9px;
      }
    }

    .overview {
      line-height: 20px;
    }
  }
}
</style>