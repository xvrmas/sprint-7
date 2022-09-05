<template>
  <div>
    <div class="carta">
      Número de páginas <b-button
        style="background-color: salmon"
        variant="outline-light"
        @click="sumaTotal1++"
        >+</b-button
      >
      <input  size="1" v-model="sumaTotal1" />
      <b-button
        class="boto"
        style="background-color: salmon"
        variant="outline-light"
        @click="sumaTotal1--"
        >-</b-button
      >
      <br /><br />
      Número de idiomas <b-button
        style="background-color: salmon"
        variant="outline-light"
        @click="sumaTotal2++"
        >+</b-button
      >
      <input size="1" v-model="sumaTotal2" />
      <b-button
        style="background-color: salmon"
        variant="outline-light"
        @click="sumaTotal2--"
        >-</b-button
      >
    </div>
  </div>
</template>
<script>
export default {
  name: "Panell",
  props: ["selected"],
  data() {
    return {
      sumaTotal1: 0,
      sumaTotal2: 0,
      paginesIdiomes: 0,
      condition: false,
    };
  },

  total: 0,
  computed: {
    sumaTotal() {
      if (this.sumaTotal1 < 0) {
        this.sumaTotal1 = 0;
      }
      if (this.sumaTotal2 < 0) {
        this.sumaTotal2 = 0;
      } else this.paginesIdiomes = this.sumaTotal1 * 30 + this.sumaTotal2 * 30;
      {
        return this.paginesIdiomes;
      }
    },
    sumaPresupost() {
      this.total = 0;
      for (let item of this.selected) {
        this.total = this.total + item;
      }
      return this.total + this.paginesIdiomes;
    },
  },
  watch: {
    sumaPresupost: function () {
      this.$emit("resultat", this.sumaPresupost);
    },
    sumaTotal() {},
  },
};
</script>
<style scoped>
.carta {
  padding: 5%;
  height: auto;
  width: fit-content;
  border: solid 3.5px;
  border-radius: 15px;
  margin-top: 1%;
  margin-bottom: 1%;
}
</style>