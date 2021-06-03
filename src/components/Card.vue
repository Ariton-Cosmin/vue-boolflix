<template>
  <div>
    <div class="flip-card">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <img
            :src="imageURL + card.poster_path"
            :alt="card.title || card.name"
          />
        </div>

        <div class="flip-card-back">
          <p><strong>Titolo: </strong> {{ card.title || card.name }}</p>

          <p>
            <strong>Titolo originale: </strong>
            {{ card.original_title || card.original_name }}
          </p>

          <p>
            <strong>Lingua: </strong>
            <img
              class="flag"
              v-if="flags.includes(card.original_language)"
              :src="require(`../assets/img/${card.original_language}.png`)"
              :alt="card.original_language"
            />
            <span v-else>{{ card.original_language }}</span>
          </p>

          <div>
            <strong>Voto: </strong>
            <div class="stars">
              <div class="empty">
                <div class="inner">
                  <i class="far fa-star"></i>
                  <i class="far fa-star"></i>
                  <i class="far fa-star"></i>
                  <i class="far fa-star"></i>
                  <i class="far fa-star"></i>
                </div>
              </div>

              <div class="solid" :style="`width:${6.7 * card.vote_average}px`">
                <div class="inner">
                  <i class="fas fa-star"></i>
                  <i class="fas fa-star"></i>
                  <i class="fas fa-star"></i>
                  <i class="fas fa-star"></i>
                  <i class="fas fa-star"></i>
                </div>
              </div>
            </div>
          </div>

          <p class="overview">
            <strong>Overview: </strong>
            {{ card.overview }}
          </p>
        </div>
      </div>
    </div>
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
      imageURL: "https://image.tmdb.org/t/p/w342",
    };
  },
};
</script>

<style lang="scss" scoped>
div {
  margin-top: 1.5rem;
  margin-bottom: 2rem;
  margin-right: 1.5rem;

  .flip-card {
    background-color: transparent;
    width: 342px;
    height: 513px;
    perspective: 1000px;
  }

  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    transition: transform 0.6s;
    transform-style: preserve-3d;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  }

  .flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
  }

  .flip-card-front,
  .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    padding: 10px;
    border: 1px solid white;
    background-color: black;
    overflow: hidden;
  }

  .flip-card-front {
    color: black;

    img {
      width: 100%;
    }
  }

  .flip-card-back {
    line-height: 2;
    color: white;
    transform: rotateY(180deg);
    overflow: scroll;

    .overview {
      line-height: 1.3;
    }
  }

  .flag {
    width: 30px;
    vertical-align: middle;
  }

  .stars {
    position: relative;
    margin-bottom: -30px;

    .empty,
    .solid {
      position: absolute;
      top: -105px;
      left: 50px;
      overflow: hidden;
    }

    .inner {
      width: 90px;
    }
  }
}
</style>