<template>
  <div class="home ml-5">
    <h4>¿Que quieres hacer?</h4>
    <div class="m-3">
      <b-form-checkbox-group
        stacked
        v-model="selected"
        :options="options"
        value-field="preu"
        text-field="name"
      ></b-form-checkbox-group>
      <h4 class="m-3">Preu: {{ sumaPresupost }} €</h4>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  data() {
    return {
      selected: [],
      options: [
        { preu: 500, name: "Una pàgina web (500 €)" },
        { preu: 300, name: "Una consultoria SEO (300€)" },
        { preu: 200, name: "Una campanya de Google Ads (200 €)" },
      ],
      total: 0,
    };
  },
  computed: {
    sumaPresupost() {
      this.total = 0;
      for (let item of this.selected) {
        this.total = this.total + item;
      }
      return this.total;
    },
  },
};
</script>
