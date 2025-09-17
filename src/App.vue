<template>
  <PieDePagina></PieDePagina>
  <encabezadoPagina></encabezadoPagina>
  <BodyDarkSouls></BodyDarkSouls>
</template>

<script>
import PieDePagina from './components/pieDePagina.vue';
import encabezadoPagina from './components/encabezadoPagina.vue';
import BodyDarkSouls from './components/Body.vue';

export default {
  name: 'App',
  components: {
    encabezadoPagina,
    BodyDarkSouls,
    PieDePagina,
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
