<template>
  <div>
    <!-- <button class="btn" @click="neteja">Neteja Busqueda</button> -->
    <div class="caixa">
      <div class="llistat">
        <div v-for="element in resultRef" :key="element.id">
          <h6>
            <strong
              >Amb la referencia "{{ element.referencia }}" tens aquest
              presupost:</strong
            >
          </h6>
          <h6>
            Nom del presupost:<strong> '{{ element.referencia }}''</strong>
          </h6>
          <h6>
            Client: <strong>{{ element.client }}</strong>
          </h6>
          <h6>
            serveis: <strong> {{ element.serveis + "" }}</strong>
          </h6>

          <h6>
            Preu: <strong> {{ element.preu }}</strong>
          </h6>
          <h6>Presupost nº:{{ element.contador }}</h6>

          <hr style="border: solid 1px" />
        </div>
      </div>
      <div v-for="element in resultNom" :key="element.id">
        <h6>
          <strong
            >Amb el nom "{{ element.client }}" tens aquest presupost:</strong
          >
        </h6>

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
          Preu: <strong> {{ element.preu }}</strong>
        </h6>
        <h6>Presupost nº:{{ element.contador }}</h6>

        <hr style="border: solid 1px" />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "busqueda",
  props: ["resultRef", "resultNom"],
  data() {
    return {
      condition: false,
    };
  },
};
</script>
<style scoped>
.caixa {
  background-color: rgb(222, 233, 243);
}
</style>