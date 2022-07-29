<template>
  <div id="app">
    <!-- RECUPERO L'emit -->
    <base-header @searching="Search" />
    <!-- PASSO I 3 Array -->
    <the-main :movies="movies" :series="series" :languages="languages" />
  </div>
</template>

<script>
import BaseHeader from "./components/BaseHeader.vue";
import TheMain from "./components/TheMain.vue";
// Import Sass
import "./assets/sass/style.scss";
// IMPORT AXIOS
import axios from "axios";

export default {
  name: "App",
  components: {
    BaseHeader,
    TheMain,
  },
  data() {
    return {
      movies: [], // Array Vuoto Film
      series: [], // Array Vuoto Serie
      languages: ["it", "en"], // array di lingue con bandierina
      api_key: "d4080a5258930f939fec89926b6aa52e", // API KEY DI AUTORIZZAZIONE MIA PERSONALE
      baseUri: "https://api.themoviedb.org/3",
    };
  },

  methods: {
    // FUNZIONE PER TROVARE I FILM
    searchMovies(query) {
      const params = {
        query: query,
        api_key: this.api_key,
        baseUri: "https://api.themoviedb.org/3",
      };
      return axios
        .get(`${this.baseUri}/search/movie`, { params })
        .then((response) => {
          this.movies = response.data.results; // api call -> salva nell'array vuoto 'movies' i dati ricevuti in risposta da axios
        });
    },

    // FUNZIONE PER TROVARE I TELEFILM
    searchSeries(query) {
      const params = {
        query: query,
        api_key: this.api_key,
      };
      return axios
        .get(`https://api.themoviedb.org/3/search/tv`, { params })
        .then((response) => {
          this.series = response.data.results; // a
        });
    },

    // FUNZIONE GENERALIZZA PER LA RICERCA
    Search(query) {
      // Controllo e svuoto
      if (!query) {
        this.movies = this.series = [];
        return;
      }
      this.searchSeries(query);
      this.searchMovies(query);
    },
  },
};
</script>

<style lang="scss">
</style>
