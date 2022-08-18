<template>
  <div>
    <div class="carta">
      Número de paginas <input id="imp1" type="number" /><br /><br />
      Número de idiomas <input id="imp2" type="number" />
    </div>
  </div>
</template>
<script>
export default {
  name: "Panell",
  props: ["selected"],
  total: 0,
  computed: {
    sumaPresupost() {
      this.total = 0;
      for (let item of this.selected) {
        this.total = this.total + item;
      }
      return this.total;
    },
  },
  watch: {
    sumaPresupost: function () {
      this.$emit("resultat", this.sumaPresupost);
    },
  },
};
</script>
<style scoped>
.carta {
  padding: 1rem;
  height: auto;
  width:fit-content;
  border: solid 3px;
  border-radius: 15px;
  margin: 1%;
}
</style>