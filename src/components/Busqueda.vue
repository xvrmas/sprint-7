<template>
  <div>
    <!-- <button class="btn" @click="neteja">Neteja Busqueda</button> -->
    <div class="caixa">
      <div class="llistat">
        <div v-for="element in resultRef" :key="element.id">
          <h6>
            <strong
              >With the reference "{{ element.referencia }}" you have this one
              budget:</strong
            >
          </h6>
          <h6>
            Budget Name:<strong> '{{ element.referencia }}''</strong>
          </h6>
          <h6>
            Customer: <strong>{{ element.client }}</strong>
          </h6>
          <h6>
            Services: <strong> {{ element.serveis + "" }}</strong>
          </h6>

          <h6>
            Price: <strong> {{ element.preu }}</strong>
          </h6>
          <h6>Budget nº:{{ element.contador }}</h6>

          <hr style="border: solid 1px" />
        </div>
      </div>
      <div v-for="element in resultNom" :key="element.id">
        <h6>
          <strong
            >With the name  "{{ element.client }}" you have this budget:</strong
          >
        </h6>

        <h6>
          <strong> {{ element.referencia }}</strong>Budget Name:
        </h6>
        <h6>
          Customer: <strong>{{ element.client }}</strong>
        </h6>
        <h6>
          Services: <strong> {{ element.serveis + "" }}</strong>
        </h6>

        <h6>
          Price: <strong> {{ element.preu }}</strong>
        </h6>
        <h6>Budget nº:{{ element.contador }}</h6>

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