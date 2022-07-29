<template>
  <div class="col-4 m-bcol d-flex justify-content-center">
    <div class="card h-100">
      <figure class="margin-0">
        <img
          class="copertina_img img-fluid"
          :src="`http://image.tmdb.org/t/p/w342/${info.poster_path}`"
        />
      </figure>

      <div id="retroCard">
        <ul class="show">
          <!-- STAMPO IMG -->

          <li class="py-1 mt-4 me-2 px-0">
            <strong
              >Titolo: {{ type === "movie" ? info.title : info.name }}
            </strong>
          </li>
          <li class="py-1 px-0 me-3">
            <strong>Titolo originale: </strong>
            <!-- TERNARIO PER VERIFICARE SE TYPE SERIE O UN FILM -->
            {{ type === "movie" ? info.original_title : info.original_name }}
          </li>
          <li class="py-1">
            <strong>Lingue: </strong>
            <!-- Cambio La bandiera a seconda se è inclusa nella mia cartella Flags o no , se no stampo la mia stringa    -->

            <!-- FLAGS -->
            <img
              v-if="languages.includes(info.original_language)"
              :src="`/img/flags/${info.original_language}.png`"
              alt="flags"
              class="flag"
            />
            <span class="text-uppercase" v-else>
              {{ info.original_language }}</span
            >
            <!-- /FLAGS -->
          </li>
          <li class="py-1">
            <strong><star-vote :vote="info.vote_average" /></strong>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import StarVote from "./StarVote.vue";
export default {
  name: "BoxCard",
  components: {
    StarVote,
  },
  props: {
    info: Object,
    // info' object per gli array di oggetti filtrati
    type: String, // Stringa per differenziare movie/serie
    languages: Array,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "@/assets/sass/style.scss";
.m-bcol {
  margin-bottom: 50px;
}
.card {
  background-color: $bg-color-black;
  opacity: 1;
  max-height: 460px;

  .copertina_img {
    max-width: 342px;
    max-height: 460px;
  }

  &:hover {
    border: 1px solid $primary-color;
    opacity: 0.2;
    width: 342px;
    transform: scale(1.1);
    transition: transform 0.4s;
  }
}

.card:hover .copertina_img {
  display: none;
}
.show {
  color: $primary-color;
  display: none;
}
.card:hover .show {
  display: block;
}

.flag {
  width: 20px;
}
</style>