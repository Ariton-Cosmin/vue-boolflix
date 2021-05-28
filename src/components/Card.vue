<template>
  <div>
    <ul>
      <li><span>Title:</span> {{ card.title }}</li>
      <li>
        <span>Original name:</span>
        {{ card.original_title || card.original_name }}
      </li>
      <li><span>Langauge:</span> {{ card.original_language }}</li>
      <li><span>Vote:</span> {{ card.vote_average }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    card: Object,
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
    }
  }
}
</style>