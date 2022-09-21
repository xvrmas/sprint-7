<template>
  <div>
    <button class="btn m-1" @click="ordenarAlfabet()">A-Z</button>
  
    <button class="btn m-1" @click="ordenarPreu()">€ +/-</button>
    <button class="btn m-1" @click="ordenarData()">
      <b-icon icon="arrow-repeat"></b-icon>
    </button>
    <!-- <button class="btn m-1" @click="cercaRef()">
      <b-icon icon="search"></b-icon>
    </button>
    <button class="btn m-1" @click="cercaNom()"><b-icon></b-icon></button> -->

    <!-- <h4>Llistat de pressupostos:</h4> -->
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
          <hr style="border: solid 1px" />
        </div>
      </div>
    </div>
  </div>
</template>
<script scoped>
export default {
  name: "presupostList",
  props: ["presupost"],
  data() {
    return {
      ordre: [],
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
    // cercaRef() {},
    // cercaNom() {},
  },
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
  border: 0;
  border-radius: 50%;
  height: 50px;
  width: auto;
}
</style>