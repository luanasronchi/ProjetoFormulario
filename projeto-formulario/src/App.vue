<template>
  <formulario/>
</template>

<script>
import Formulario from "./components/Formulario.vue";

export default {
  name: "App",
  components: {
    Formulario,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
