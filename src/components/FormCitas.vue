<template>
  <main id="app" class="container text-center py-3">
    <form @submit.prevent="agregarCita" class="formulario-citas">
      <div class="form-row">
        <div class="form-group">
          <label :class="{ rojo: !paciente }">Paciente:</label>
          <input type="text" v-model="paciente" required />
        </div>
        <div class="form-group">
          <label :class="{ rojo: !fecha }">Fecha:</label>
          <input type="date" v-model="fecha" required />
        </div>
        <div class="form-group">
          <label :class="{ rojo: !hora }">Hora:</label>
          <input type="time" v-model="hora" required />
        </div>
        <div class="form-group">
          <label :class="{ rojo: !gravedad }">Gravedad:</label>
          <select v-model="gravedad" required>
            <option value="">Seleccionar</option>
            <option value="Baja">Baja</option>
            <option value="Media">Media</option>
            <option value="Alta">Alta</option>
          </select>
        </div>
        <div class="form-group">
          <label :class="{ rojo: !motivo }">Motivo:</label>
          <input type="text" v-model="motivo" required />
        </div>
      </div>
      <div class="py-3">
        <button
          type="submit"
          class="btn btn-dark my-3"
          :disabled="!formularioCompleto"
        >
          Agregar
        </button>
      </div>
    </form>
    <p v-if="citas.length === 0">Aún no hay consultas registradas</p>
  </main>
</template>

<script>
export default {
  data() {
    return {
      paciente: "",
      fecha: "",
      hora: "",
      gravedad: "",
      motivo: "",
    };
  },
  props: {
    citas: {
      type: Array,
      required: true,
    },
  },
  computed: {
    formularioCompleto() {
      return (
        this.paciente && this.fecha && this.hora && this.gravedad && this.motivo
      );
    },
  },
  methods: {
    agregarCita() {
      const nuevaCita = {
        paciente: this.paciente,
        fecha: this.fecha,
        hora: this.hora,
        gravedad: this.gravedad,
        motivo: this.motivo,
      };
      this.$emit("agregar", nuevaCita);
      this.limpiarFormulario();
    },
    limpiarFormulario() {
      this.paciente = "";
      this.fecha = "";
      this.hora = "";
      this.gravedad = "";
      this.motivo = "";
    },
  },
};
</script>

<style scoped>
.formulario-citas {
  border: 1px solid #ddd;
  border-radius: 0.5rem;
  padding: 1rem;
  background-color: #f9f9f9;
}

.form-row {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 1rem;
}

.form-group {
  flex: 1;
  margin: 0.5rem;
  min-width: 150px;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: bold;
}

.form-group input,
.form-group select,
.form-group textarea {
  width: 80%;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 0.25rem;
}

.rojo {
  color: red;
}
</style>
