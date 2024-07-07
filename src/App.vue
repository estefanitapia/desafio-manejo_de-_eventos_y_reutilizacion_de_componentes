<template>
  <div id="app">
    <h1>Administrador de Citas Médicas</h1>
    <FormCitas @agregar="agregarCita" :citas="citas" />
    <hr>
    <ListaCitas :citas="citas" @eliminar="eliminarCita" />
  </div>
</template>
<script>
import FormCitas from './components/FormCitas.vue';
import ListaCitas from './components/ListaCitas.vue';

export default {
  name: 'App',
  components: {
    FormCitas,
    ListaCitas
  },
  data() {
    return {
      citas: []
    };
  },
  methods: {
    agregarCita(nuevaCita) {
      this.citas.push(nuevaCita);
    },
    eliminarCita(index) {
      this.citas.splice(index, 1);
    }
  }
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  margin: 0 auto;
  padding: 20px;
}
h1 {
  text-align: center;
  color: #333;
}
hr {
  margin-top: 20px;
  margin-bottom: 20px;
  border: 0;
  border-top: 1px solid #ccc;
}
</style>