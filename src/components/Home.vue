<template>
  <div class="contenidor">
    <div class="home ml-4">
      <h4>¿Qué quieres hacer?</h4>
      <div class="mt-3">
        <b-form-checkbox
          class="check"
          id="1"
          name="Una pàgina web"
          v-model="selected"
          @change="showPanel(), clicat('Una pàgina web'), updateCheck()"
          :value="500"
          >Una pàgina web (500 €)</b-form-checkbox
        >
        <panell
          :selected="selected"
          @resultat="totalSuma"
          :condition="condition"
        ></panell>

        <b-form-checkbox
          class="check"
          id="2"
          name="Una consultoria SEO"
          @change="clicat('Una consultoria SEO'), updateCheck()"
          v-model="selected"
          :value="300"
          >Una consultoria SEO (300 €)</b-form-checkbox
        >
        <b-form-checkbox
          class="check"
          id="3"
          name="Una campanya de Google Ads"
          @change="clicat('Una campanya de Google Ads'), updateCheck()"
          v-model="selected"
          :value="200"
          >Una campanya de Google Ads (200 €)</b-form-checkbox
        >
        <div>
          <br />
          <h5>Preu:{{ resultat }} €</h5>
        </div>
      </div>
      <div>
        <p>
          Si lo desea puede guardar el presupuesto ingresando el nombre del
          cliente<br />
          y una referencía.
        </p>
        <b-form-input
          type="text"
          v-model="referencia"
          placeholder="Referencia del presupuesto"
        ></b-form-input>
        <b-form-input
          type="text"
          class="mt-3 mb-4"
          v-model="client"
          placeholder="Nombre del cliente"
        ></b-form-input>
        <button class="btn m-1" @click="guardar()">Guardar</button>
        <button class="btn m-1" @click="Home">Inicio</button>
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
      client: "",
      referencia: "",
      resultat: 0,
      counter: 0,
      preu: 0,
      condition: false,
      trobat: false,
      isCheck: false,
      textServei: "",
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
    Home() {
      this.$router.push("/");
    },
    showPanel() {
      this.counter++;
      console.log(this.counter);
      if (this.counter % 2 == 0) {
        this.condition = false;
      } else {
        this.condition = true;
      }
    },
    guardar() {
      var pressupostList = {
        referencia: this.referencia,
        client: this.client,
        preu: this.resultat,
        serveis: this.arrayServei,
      };
      this.arrayPresupost.push(pressupostList),
        (this.client = ""),
        (this.referencia = "");
      this.condition = false;
      this.resetCheck();
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
        document.getElementById("1").checked = false;
        document.getElementById("2").checked = false;
        document.getElementById("3").checked = false;
        this.arrayServei=[],
        this.selected=[],
        this.counter=0
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
