<template>
  <header>
    <div class="container">
      <h1>BOOLFLIX</h1>

      <div class="input">
        <input v-model.trim="textSearch" type="text" placeholder="Cerca..." />
      </div>

      <div class="button">
        <button
          @click="$emit('startSearch', { text: textSearch, type: 'movie' })"
        >
          Film
        </button>
        <button @click="$emit('startSearch', { text: textSearch, type: 'tv' })">
          Serie
        </button>
        <button
          @click="$emit('startSearch', { text: textSearch, type: 'all' })"
        >
          Tutto
        </button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Head",
  data() {
    return {
      textSearch: "",
    };
  },
};
</script>

<style lang="scss" scoped>
header {
  position: fixed;
  width: 100%;
  height: 70px;
  background-color: black;
}

.container {
  display: flex;
  justify-content: center;
  line-height: 70px;

  h1 {
    margin-right: 10rem;
    color: red;
  }

  .input {
    width: 20%;
    margin-left: 10rem;

    input {
      width: 100%;
      height: 40px;
      padding-left: 1rem;
      border-radius: 5px;
      border: none;
      outline-width: 0;
    }
  }

  .button {
    width: 25rem;

    button {
      width: 60px;
      height: 40px;
      margin-left: 1rem;
      border: none;
      text-transform: uppercase;
      border-radius: 5px;
      cursor: pointer;
      color: white;
      background-color: blue;
      &:hover {
        background-color: rgb(2, 82, 255);
      }
    }
  }
}
</style>