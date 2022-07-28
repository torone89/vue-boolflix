<template>
  <div class="hello">
    <ul>
      <li>
        <strong
          >Titolo: {{ type === "movie" ? info.title : info.name }}
        </strong>
      </li>
      <li>
        <strong>Titolo originale: </strong>
        <!-- TERNARIO PER VERIFICARE SE TYPE SERIE O UN FILM -->
        {{ type === "movie" ? info.original_title : info.original_name }}
      </li>
      <li>
        <strong>Lingue:</strong>
        <!-- Cambio La bandiera a seconda se è inclusa nella mia cartella Flags o no , se no stampo la mia stringa    -->

        <!-- FLAGS -->
        <img
          v-if="languages.includes(info.original_language)"
          :src="`/img/flags/${info.original_language}.png`"
          alt="flags"
        />
        <span class="text-uppercase" v-else> {{ info.original_language }}</span>
        <!-- /FLAGS -->
      </li>
      <li>
        <strong>Voto:{{ info.vote_average }}</strong>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "BoxCard",
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
</style>