<template>
  <div>
    <div>
      <!-- INPUT SEARCH -->
      <input
        v-model="keyword"
        @keyup.enter="searchKeyword"
        type="text"
        class="form-control rounded"
        placeholder="Cerca il tuo film"
        aria-label="Search"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "BaseHeader",
  data() {
    return {
      keyword: "", // Dinamica in base al testo digitato nell'input
    };
  },
  methods: {
    searchKeyword() {
      this.$emit("searching", this.keyword); // searchKeyword farà l'emit. / Richiamo metodo nell'input
      //   il $emit passa dal figlio (Header) al padre (App.vue) il nome dell'avento (searching)'
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>