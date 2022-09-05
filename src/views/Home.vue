<template>
  <div class="home ml-4">
    <h4>¿Qué quieres hacer?</h4>
    <div class="m-3">
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
  </div>
</template>

<script>
import Panell from "@/components/Panell.vue";
export default {
  components: { Panell },
  name: "HomeView",
  data() {
    return {
      selected: [],
      resultat: 0,
    };
  },

  methods: {
    totalSuma(value) {
      this.resultat = value;
    },
  },
};
</script>
<style>
  h4{
    margin-left: 2%;
  }
</style>
