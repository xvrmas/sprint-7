<template>
  <div>
    <h4>Llistat de pressupostos:</h4>
    <hr style="border: solid 1px" />
    <div class="caixa">
      <div class="llistat">
        <div v-for="element in presupost" :key="element.id">
          <h6>
            Data del presupost: <strong>{{element.data}}</strong>
          </h6>
          <h6>
            Nom del presupost:<strong> {{ element.referencia }}</strong>
          </h6>
          <h6>
            Client: <strong>{{ element.client }}</strong>
          </h6>
          <h6>
            serveis: <strong> {{ element.serveis + "," }}</strong>
          </h6>
          <h6>
            Nº de pagines:<strong>{{ element.pagines }}</strong>
          </h6>
          <h6>
            Idiomes:<strong>{{ element.idiomes }}</strong>
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
<script>
export default {
  name: "presupostList",
  props: ["presupost"],
};
</script>
<style>
.llistat {
  margin: 10px;
}
</style>