<template>
  <!-- STARS -->
  <div>
    <strong>Voto:</strong>
    <i
      v-for="star in starsCalc"
      :key="star"
      class="fas fa-star ms-1 fa-yellow"
    ></i>
  </div>
  <!-- / STARS -->
</template>


<script>
export default {
  name: "StarVote",
  props: {
    vote: Number,
  },
  computed: {
    //   Funzione per calcolarmi un punteggio media di stelle .. Divido per due e
    // calcolo una media su 5 stelle arrotondando per eccesso cn Math.ceil
    starsCalc() {
      return Math.ceil(this.vote / 2);
    },
  },
};
</script>

<style lang="scss">
.fa-yellow {
  color: yellow;
}
</style>