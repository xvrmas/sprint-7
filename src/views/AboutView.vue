<template>
  <div class="careta">
    <div class="bg-primary">
      
    </div>
    <div class="container  px-5 px-lg-5 mt-5">
      <div class="card px-4 mb-3 shadow">
        <div class="card-body px-3 p-4">
          <div class="text-center">
            <h3>¿Que quieres hacer?</h3>
            <h4 class="fw-bolder">¿Una pagina web, una consultoría SEO o una campanya de Google Ads? </h4>
            <h5>En "obtener presupuesto" podrás seleccionar las opciones que se adapten a tus necesidades"</h5>
            <h4></h4>
          </div>
        </div>
      </div>
        </div>
    <button class="btn" @click="Calculadora">Obtener presupuesto</button>
  </div>
</template>

<script>
import Home from "@/components/Home.vue";
export default {
  components: { Home },
  name: "AboutView",
  methods: {
    Calculadora() {
      this.$router.push("/Home");
    },
  },
};
</script>
<style scoped>

.careta {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  background-color: #79c2d0;
  border: solid 0.1em #68b3bf;
  border-radius: 1em;
  font-family:serif;
}


.btn {
  background-color: #6c5b7c;
  color: white;
  border: 0;
  border-radius: 1em;
  width: 8em;
  height:4em;
  margin-bottom: 2em;
  font-size: 1.2em;
}

.card{
  border-radius: 1em;
}
</style>
