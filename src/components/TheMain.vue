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