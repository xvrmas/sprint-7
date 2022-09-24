<template>
  <div>
    <button class="btn m-1" @click="ordenarAlfabet()">A-Z</button>

    <button class="btn m-1" @click="ordenarPreu()">€ +/-</button>
    <button class="btn m-1" @click="ordenarData()">
      <b-icon icon="arrow-repeat"></b-icon></button
    ><br />
    <button class="btn m-1" @click="cercaRef()">
      <b-icon icon="search"></b-icon>
    </button>
    <input
      v-model="texteRef"
      id="cercaReferencia"
      placeholder="Entra una referencia"
    /><br />
    <button class="btn m-1" @click="cercaNom()">
      <b-icon icon="search"></b-icon>
    </button>
    <input type="text" v-model="textNom" placeholder="Entra un nom" />
    <busqueda :resultRef="resultRef" :resultNom="resultNom"></busqueda>

    <h4>Llistat de pressupostos:</h4>
    <hr style="border: solid 1px" />
    <div class="caixa">
      <div class="llistat">
        <div v-for="element in presupost" :key="element.id">
          <h6>
            Nom del presupost:<strong> {{ element.referencia }}</strong>
          </h6>
          <h6>
            Client: <strong>{{ element.client }}</strong>
          </h6>
          <h6>
            serveis: <strong> {{ element.serveis + "" }}</strong>
          </h6>
          <h6>
            Nº de pagines:<strong>{{ element.pagines }}</strong>
          </h6>
          <h6>
            Idiomes:<strong>{{ element.idiomes }}</strong>
          </h6>
          <h6>
            Data del presupost: <strong>{{ element.diaHora }}</strong>
          </h6>
          <h6>
            Preu: <strong> {{ element.preu }}</strong>
          </h6>
          <h6>Presupost nº:{{ element.contador }}</h6>

          <hr style="border: solid 1px" />
        </div>
      </div>
    </div>
  </div>
</template>
<script >
import Busqueda from "@/components/Busqueda.vue";
export default {
  components: { Busqueda },
  name: "presupostList",
  props: ["presupost"],

  data() {
    return {
      ordre: [],
      i: 0,
      arrayReferencia: [],
      texteRef: [],
      textNom: [],
      resultRef: [],
      resultNom: [],
    };
  },
  methods: {
    ordenarAlfabet() {
      this.presupost.sort((a, b) => {
        if (a.referencia.toLowerCase() > b.referencia.toLowerCase()) {
          return 1;
        }
        if (a.referencia.toLowerCase() < b.referencia.toLowerCase()) {
          return -1;
        }
        return 0;
      });
    },
    ordenarData() {
      this.presupost.sort((a, b) => {
        if (a.diaHora > b.diaHora) {
          return 1;
        }
        if (a.diaHora < b.diaHora) {
          return -1;
        }
        return 0;
      });
    },
    ordenarPreu() {
      this.presupost.sort((a, b) => {
        if (a.preu > b.preu) {
          return -1;
        }
        if (a.preu < b.preu) {
          return 1;
        }
        return 0;
      });
    },
    cercaRef() {
      this.resultRef = this.presupost.filter(
        (element) => element.referencia == this.texteRef
      );
      this.texteRef = "";
    },
    cercaNom() {
      this.resultNom = this.presupost.filter(
        (element) => element.client == this.textNom
      );
      this.textNom = "";
    },
  },

  watch: {},
};
</script>
<style scoped>
body {
  display: grid;
  align-content: center;
  text-align: center;
}
.llistat {
  margin: 10px;
}
.btn {
  background-color: salmon;
  color: white;
  height: 40px;
  width: auto;
}
</style>