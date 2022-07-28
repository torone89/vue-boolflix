<template>
  <div class="prova">
    <!-- COMPONENTE PER CREARE LE CART E V-FOR LOGICA -->
    <box-card />
  </div>
</template>

<script>
import BoxCard from "./BoxCard.vue";
export default {
  components: {
    BoxCard,
  },
  name: "TheMain",
  props: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>