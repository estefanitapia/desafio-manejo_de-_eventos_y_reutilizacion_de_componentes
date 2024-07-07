<template>
  <div>
    <p><strong>Paciente</strong></p>
    <p>{{ cita.paciente }}</p>
    <p><strong>Fecha</strong></p>
    <p>{{ formatoFecha(cita.fecha) }}</p>
    <p><strong>Hora</strong></p>
    <p>{{ cita.hora }}</p>
    <p><strong>Gravedad</strong></p>
    <p>{{ cita.gravedad }}</p>
    <p><strong>Motivo</strong></p>
    <p>{{ cita.motivo }}</p>
    <button @click="eliminarCita">Eliminar</button>
  </div>
</template>

<script>
import { formatoFecha } from "../utils";

export default {
  props: {
    cita: {
      type: Object,
      required: true,
    },
  },
  methods: {
    eliminarCita() {
      this.$emit("eliminar");
    },
    formatoFecha,
  },
};
</script>

<style scoped>
p {
  justify-self: auto;
  text-align: center;
}
</style>
