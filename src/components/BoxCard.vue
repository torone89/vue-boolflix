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
        <strong>Lingua: {{ info.original_language }}</strong>
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
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>