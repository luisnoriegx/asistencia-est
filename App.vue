<template>
  <div class="container">
    <h1 class="title">Lista de Asistencia</h1>
    <table>
      <thead>
        <tr>
          <th>Apellidos</th>
          <th>Nombres</th>
          <th>Asistencia</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(estudiante, index) in estudiantes" :key="index" 
            :class="{'asistio': estudiante.asistio === true, 'no-asistio': estudiante.asistio === false}">
          <td>{{ estudiante.apellido }}</td>
          <td>{{ estudiante.nombre }}</td>
          <td>
            <label>
              <input type="radio" :name="'asistencia' + index" :value="true" v-model="estudiante.asistio" /> Asistió
            </label>
            <label>
              <input type="radio" :name="'asistencia' + index" :value="false" v-model="estudiante.asistio" /> No asistió
            </label>
          </td>
        </tr>
      </tbody>
    </table>
    <div class="contador">
      <p>Asistieron: {{ totalAsistieron }}</p>
      <p>No asistieron: {{ totalNoAsistieron }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      estudiantes: [
        { apellido: 'Ramírez', nombre: 'Juan', asistio: null },
        { apellido: 'González', nombre: 'Lucía', asistio: null },
        { apellido: 'Fernández', nombre: 'Pedro', asistio: null },
        { apellido: 'Martínez', nombre: 'Carla', asistio: null },
        { apellido: 'López', nombre: 'Andrés', asistio: null }
      ]
    };
  },
  computed: {
    totalAsistieron() {
      return this.estudiantes.filter(e => e.asistio === true).length;
    },
    totalNoAsistieron() {
      return this.estudiantes.filter(e => e.asistio === false).length;
    }
  }
};
</script>

<style scoped>
.container {
  max-width: 500px;
  margin: 20px auto;
  padding: 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  text-align: center;
}
.title {
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 10px;
}
table {
  width: 100%;
  border-collapse: collapse;
}
th, td {
  border: 1px solid #ddd;
  padding: 8px;
}
th {
  background-color: #f3f4f6;
}
.asistio {
  background-color: #c6f6d5 !important;
}
.no-asistio {
  background-color: #feb2b2 !important;
}
.contador {
  margin-top: 15px;
  font-size: 16px;
  font-weight: bold;
}
</style>
