<template>
  <div class="lista-card">
    <div
      v-for="(cita, index) in citas"
      :key="index"
      class="cita-card"
      :class="cita.gravedad.toLowerCase()"
    >
      <CitaCard :cita="cita" @eliminar="eliminarCita(index)" />
    </div>
    <p id="warning" v-if="citas.length === 0">Aún no hay citas registradas.</p>
  </div>
</template>

<script>
import CitaCard from "./CitaCard.vue";

export default {
  components: {
    CitaCard,
  },
  props: {
    citas: {
      type: Array,
      required: true,
    },
  },
  methods: {
    eliminarCita(index) {
      const nuevasCitas = [...this.citas];
      nuevasCitas.splice(index, 1);
      this.$emit("eliminar", nuevasCitas);
    },
  },
};
</script>

<style scoped>
.baja {
  background-color: #aeff2f;
}

.media {
  background-color: #ffff00;
}

.alta {
  background-color: #fe0100;
  color: white;
}
#warning {
  color: red;
}

.cita-card {
  margin: 10px;
  padding: 2rem;
  border-radius: 1rem;
  display: flex;
  justify-content: space-around;
  align-items: center;
}
.lista-card {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  overflow: auto;
}
</style>
