<template>
  <div class="contenidor">
    <div class="home ml-4">
      <h4>What do you want to do?</h4>
      <div class="mt-3">
        <b-form-checkbox
          class="check"
          v-model="selected"
          @change="
            showPanel(), clicat('A web page'), updateCheck(), diaHoraPresu()
          "
          :value="500"
          >A web page (500 €)</b-form-checkbox
        >
        <panell
          :selected="selected"
          @resultat="totalSuma"
          @pagines="numPagines"
          @idiomes="numIdiomes"
          :condition="condition"
        ></panell>

        <b-form-checkbox
          class="check"
          @change="clicat('An SEO consultancy'), updateCheck(), diaHoraPresu()"
          v-model="selected"
          :value="300"
          >An SEO consultancy (300 €)</b-form-checkbox
        >
        <b-form-checkbox
          class="check"
          @change="
            clicat('A Google Ads campaign'), updateCheck(), diaHoraPresu()
          "
          v-model="selected"
          :value="200"
          >A Google Ads campaign (200 €)</b-form-checkbox
        >
        <div>
          <br />
          <h5>Price:{{ resultat }} €</h5>
        </div>
      </div>
      <div>
        <hr style="border: solid 1px" />
        <p>
          If you wish, you can save the estimate by entering the customer's name
          and a reference.
        </p>
        <b-form-input
          type="text"
          v-model="referencia"
          placeholder="Budget reference, maximum 5 characters"
          maxlength="5"
        ></b-form-input>
        <b-form-input
          type="text"
          class="mt-3 mb-4"
          v-model="client"
          placeholder="Customer number"
          maxlength="25"
        ></b-form-input>
        <button class="btn m-1" @click="guardar()">Save</button>
        <button class="btn m-1" @click="Home">Start</button>
      </div>
    </div>
    <div class="presupost">
      <pressupostList :presupost="arrayPresupost"> </pressupostList>
    </div>
  </div>
</template>

<script>
import Panell from "@/components/Panell.vue";
import pressupostList from "@/components/pressupostList.vue";
export default {
  components: { Panell, pressupostList },
  name: "Home",
  data() {
    return {
      selected: [],
      arrayPresupost: [],
      arrayServei: [],
      arrayCheck: [],
      checkRepeat: [],
      client: "",
      referencia: "",
      textServei: "",
      diaHora: "",
      valorRef: "",
      resultat: 0,
      counter: 0,
      preu: 0,
      pagines: 0,
      idiomes: 0,
      contador: 1,
      condition: false,
      trobat: false,
      isCheck: false,
      trobatRef: false,
    };
  },

  methods: {
    clicat(id) {
      var i = 0;
      while (i <= this.arrayServei.length && !this.trobat) {
        if (this.arrayServei[i] == id) {
          this.trobat = true;
        }
        i++;
      }
      if (this.trobat == true) {
        this.arrayServei.splice(i - 1, 1);
      } else {
        this.arrayServei.push(id);
      }
      this.trobat = false;
      return this.arrayServei;
    },
    totalSuma(value) {
      this.resultat = value;
    },
    numPagines(value) {
      this.pagines = value;
    },
    numIdiomes(value) {
      this.idiomes = value;
    },
    Home() {
      this.$router.push("/");
    },
    showPanel() {
      this.counter++;
      if (this.counter % 2 == 0) {
        this.condition = false;
      } else {
        this.condition = true;
      }
    },
    diaHoraPresu() {
      this.diaHora = new Date().toUTCString();
      return this.diaHora;
    },
    guardar() {
      var i = 0;

      var pressupostList = {
        diaHora: this.diaHora,
        referencia: this.referencia,
        client: this.client,
        preu: this.resultat,
        serveis: this.arrayServei,
        pagines: this.pagines,
        idiomes: this.idiomes,
        contador: this.contador,
      };
      this.checkRepeat = this.arrayPresupost.map(
        (element) => element.referencia
      );
      console.log(this.checkRepeat);
      for (this.valorRef of this.checkRepeat) {
        if (this.valorRef == this.referencia) {
          this.trobatRef = true;
        }
      }

      if (this.arrayServei == 0 && this.client == "" && this.referencia == "") {
        alert(
          "No se puede guardar un presupuesto vacio.Elija un servicio y rellene los campos referencia y nombre"
        );
      } else if (this.arrayServei.length == 0) {
        alert(
          "Para guardar un presupuesto primero debe elegir almenos un servicio"
        );
      } else if (this.client == "" && this.referencia == "") {
        alert("Los campos 'referencia' y 'nombre' no pueden estar vacios");
      } else if (this.referencia == "") {
        alert("Introduzca una referencia");
      } else if (this.client == "") {
        alert("Introduzca su nombre");
      } else if (this.trobatRef == true) {
        alert(
          "Ja existeix un presupost amb aquest nom de referencia,trian un altre"
        );
        this.referencia = "";
        this.trobatRef = false;
      } else {
        this.arrayPresupost.push(pressupostList), this.contador++;

        (this.client = ""), (this.referencia = "");
        this.condition = false;
        this.resetCheck();
      }

      return this.arrayPresupost;
    },

    updateCheck() {
      if (this.arrayServei.length >= 1) {
        this.isCheck = true;
      } else {
        this.isCheck = false;
      }
    },
    resetCheck() {
      if (this.isCheck == true) {
        document.getElementsByClassName("check").checked = false;

        (this.arrayServei = []), (this.selected = []), (this.counter = 0);
      }
    },
  },
};
</script>
<style scoped>
body {
  display: grid;
  align-content: center;
  text-align: center;
}

h4 {
  margin-left: 2%;
}
.btn {
  background-color: salmon;
  color: white;
  border: 0;
  border-radius: 50px;
  width: 200px;
}
.contenidor {
  display: grid;
  grid-template-columns: 2fr 2fr;
}
.presupost {
  margin: 20px;
}
@media (max-width: 750px) {
  .contenidor {
    display: grid;
    grid-template-columns: auto;
  }
}
</style>
