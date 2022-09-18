<template>
  <div>
    <h4>Llistat de presupostos:</h4>

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
            serveis: <strong> {{ element.serveis }}</strong>
          </h6>
          <h6>
           Nº de pagines:<strong></strong>
          </h6>
          <h6>
            Idiomes:<strong></strong>
          </h6>
          <h6>
            Preu: <strong> {{ element.preu }}</strong>
          </h6>
          <hr />
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
.caixa {
  border: solid 0.1px;
  border-radius: 2%;
}
.llistat{
  margin:10px
}
</style>