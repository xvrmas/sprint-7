<template>
  <div class="contenidor">
    <div class="home ml-4">
      <h4>¿Qué quieres hacer?</h4>
      <div class="mt-3">
        <b-form-checkbox v-model="selected" :value="500"
          >Una pàgina web (500 €)</b-form-checkbox
        >
        <panell :selected="selected" @resultat="totalSuma"></panell>

        <b-form-checkbox v-model="selected" :value="300"
          >Una consultoria SEO (300 €)</b-form-checkbox
        >
        <b-form-checkbox v-model="selected" :value="200"
          >Una campanya de Google Ads (200 €)</b-form-checkbox
        >
        <div>
          <br />
          <h5>Preu:{{ resultat }} €</h5>
        </div>
      </div>
      <div>
        <p>Si lo desea puede guardar el presupuesto ingresando el nombre del cliente<br> y una referencía.</p>
        <b-form-input
          v-model="text1"
          placeholder="Nombre del cliente"
        ></b-form-input>
        <b-form-input
          class="mt-3"
          v-model="text2"
          placeholder="referencia del presupuesto"
        ></b-form-input>
        <button class="btn m-1">Guardar</button>
        <button class="btn m-1" @click="Home">Inicio</button>
      </div>
    </div>
    <div class="presupost">
      <pressupostList :text1="text1" :text2="text2"> </pressupostList>
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
      resultat: 0,
      text1:'',
      text2:''

    };
  },

  methods: {
    totalSuma(value) {
      this.resultat = value;
    },
    Home() {
      this.$router.push("/");
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
  /* border: solid 1px; */
  margin-right: 20px;
}
@media (max-width: 600px) {
  .contenidor{
    display: grid;
    grid-template-columns: auto;
  }
  
}
</style>
