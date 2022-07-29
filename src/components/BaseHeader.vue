<template>
  <header>
    <div class="container h-100">
      <div class="row h-100">
        <div class="col-7 d-flex align-items-center">
          <figure class="m-0">
            <img src="/logo.png" alt="Logo Netflix" class="img-fluid" />
          </figure>
          <ul class="list-unstyled d-flex align-items-center m-0">
            <li class="px-3">
              <a href="#">Home</a>
            </li>
            <li class="px-3">
              <a href="#">Film</a>
            </li>
            <li class="px-3">
              <a href="#">Serie Tv</a>
            </li>
            <li class="px-3">
              <a href="#">Nuovi e popolari</a>
            </li>
            <li class="px-3">
              <a href="#">La mia lista</a>
            </li>
          </ul>
        </div>

        <div class="col-5 d-flex align-items-center justify-content-end">
          <!-- INPUT SEARCH -->
          <div class="d-flex">
            <input
              v-model="keyword"
              @keyup.enter="searchKeyword"
              type="text"
              class="form-control rounded"
              placeholder="Cerca"
              aria-label="Search"
            />

            <button
              @click="searchKeyword"
              type="button"
              class="btn text-light btn-outline-danger rounded"
            >
              Cerca
            </button>
          </div>
        </div>
      </div>
    </div>
  </header>
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
@import "@/assets/sass/style.scss";
header {
  height: 80px;
  background-color: $bg-color-header;
}
img {
  max-height: 50px;
  width: 200px;
}

li {
  height: 100%;
  font-size: 14px;
  text-transform: uppercase;
  &:hover {
    font-weight: bold;
  }

  a {
    color: $primary-color;
    &:hover {
      color: $secondary-color;
    }
  }
}
</style>