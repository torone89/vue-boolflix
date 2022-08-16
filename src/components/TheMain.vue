<template>
  <main>
    <div class="container">
      <!-- COMPONENTE PER CREARE LE CART E V-FOR LOGICA -->
      <!-- / FILM -->

      <div>
        <h2 class="text-light p-4">FILM</h2>
      </div>
      <div class="row justify-space-between">
        <box-card
          v-for="movie in movies"
          :key="movie.id"
          :info="movie"
          :type="'movie'"
          :languages="languages"
          :cast="GetCast(movie.id)"
        />
      </div>

      <!-- SERIE TV -->
      <div>
        <h2 class="text-light p-4">SERIE TV</h2>
      </div>
      <div class="row justify-space-between">
        <box-card
          v-for="serie in series"
          :key="serie.id"
          :info="serie"
          :type="'serie'"
          :languages="languages"
          :cast="GetCastTV(serie.id)"
        />
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";

import BoxCard from "./BoxCard.vue";
export default {
  components: {
    BoxCard,
  },
  name: "TheMain",
  props: {
    movies: Array, // importiamo i dati dal padre App.Vue
    series: Array,
    languages: Array,
  },
  methods: {
    // FUNZIONE PER OTTENERE IL CAST DALL'api Key
    GetCast(id) {
      axios
        .get(
          `https://api.themoviedb.org/3/movie/${id}/credits?api_key=d4080a5258930f939fec89926b6aa52e`
        )
        .then((results) => {
          this.cast = results.data.cast;
          // MAssimo 5 Elementi del cast
          this.cast?.splice(5);
        });
      return this.cast;
    },
    GetCastTV(id) {
      axios
        .get(
          `https://api.themoviedb.org/3/tv/${id}/credits?api_key=d4080a5258930f939fec89926b6aa52e`
        )
        .then((results) => {
          this.cast = results.data.cast;
          // MAssimo 5 Elementi del cast
          this.cast?.splice(5);
        });
      return this.cast;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>