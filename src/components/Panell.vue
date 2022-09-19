<template>
  <div>
    <div class="carta" v-if="condition">
      Número de páginas
      <b-button
        style="
          background-color: salmon;
          font-family: Times New Roman;
          border-radius: 25%;
        "
        variant="outline-light"
        @click="sumaTotal1++"
        >+</b-button
      >
      <input size="1" class="caixa" v-model="sumaTotal1" />
      <b-button
        class="boto"
        style="
          background-color: salmon;
          font-family: Times New Roman;
          border-radius: 25%;
        "
        variant="outline-light"
        @click="sumaTotal1--"
        >-</b-button
      >
      <b-button class="btn-modal" v-b-modal.modal-center1 rounded> i</b-button>
      <b-modal id="modal-center1" centered hide-footer hide-header>
        <p class="my-4">
          En este componente debe indicar el número de páginas que tendrá su
          sitio web
        </p>
      </b-modal>

      <br /><br />
      Número de idiomas
      <b-button
        style="
          background-color: salmon;
          font-family: Times New Roman;
          border-radius: 25%;
        "
        variant="outline-light"
        @click="sumaTotal2++"
        >+</b-button
      >
      <input size="1" class="caixa" v-model="sumaTotal2" />
      <b-button
        style="
          background-color: salmon;
          font-family: Times New Roman;
          border-radius: 25%;
        "
        variant="outline-light"
        @click="sumaTotal2--"
        >-</b-button
      >
      <b-button class="btn-modal" v-b-modal.modal-center2>i</b-button>
      <b-modal id="modal-center2" centered hide-footer hide-header>
        <p class="my-4">
          En este componente debe indicar el número de idiomas que tendrá su
          sitio web
        </p>
      </b-modal>
    </div>
  </div>
</template>
<script>
export default {
  name: "Panell",
  props: ["selected", "condition"],
  data() {
    return {
      sumaTotal1: 1,
      sumaTotal2: 1,
      paginesIdiomes: 0,
    };
  },

  total: 0,
  computed: {
    sumaTotal() {
      if (this.sumaTotal1 < 1) {
        this.sumaTotal1 = 1;
      }
      if (this.sumaTotal2 < 0) {
        this.sumaTotal2 = 0;
      }
      if (this.condition == true) {
        this.sumaTotal2 = 1;
      }
      if (this.condition == false) {
        this.sumaTotal1 = 0;
        this.sumaTotal2 = 0;
        this.paginesIdiomes = 0;
      } else this.paginesIdiomes = this.sumaTotal1 * this.sumaTotal2 * 30;
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

    sumaTotal: function () {
      this.$emit("pagines", this.sumaTotal1);
      this.$emit("idiomes", this.sumaTotal2);
    },
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
.btn-modal {
  height: 28px;
  line-height: 1px;
  border-radius: 50%;
  margin-left: 5px;
  font-family: "Times New Roman";
  font-size: large;
  font-weight: bold;
}
.caixa {
  border: 0;
}
</style>