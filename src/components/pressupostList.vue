<template>
  <div>
    <h4>Llistat de presupostos: </h4>
    <div v-for="element in presupost" :key="element.id">
      <h6>
        Nom del presupost:<strong> {{ element.referencia }}</strong>
      </h6>
      <h6>
        Client: <strong>{{ element.client }}</strong>
      </h6>
      <h6>
        serveis: <strong> {{ "aquí van els serveis contractats" }}</strong>
      </h6>
      <h6>
        Preu: <strong> {{ element.preu }}</strong>
      </h6>
      <hr />
    </div>
  </div>
</template>
<script>
export default {
  name: "presupostList",
  props: ["presupost"],
};
</script>
<style>
</style>