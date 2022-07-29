<template>
  <main>
    <div class="container">
      <!-- COMPONENTE PER CREARE LE CART E V-FOR LOGICA -->
      <!-- / FILM -->

      <div>
        <h4 class="text-light text-center p-4">Film:</h4>
      </div>
      <div class="row justify-space-between">
        <box-card
          v-for="movie in movies"
          :key="movie.id"
          :info="movie"
          :type="'movie'"
          :languages="languages"
        />
      </div>

      <!-- SERIE TV -->
      <div>
        <h4 class="text-light text-center p-5">Serie Tv:</h4>
      </div>
      <div class="row justify-space-between">
        <box-card
          v-for="serie in series"
          :key="serie.id"
          :info="serie"
          :type="'serie'"
          :languages="languages"
        />
      </div>
    </div>
  </main>
</template>

<script>
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
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>