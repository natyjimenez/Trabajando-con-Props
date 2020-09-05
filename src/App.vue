<template>
  <div class="contenido">
    <h1 class="Título">Lista de Tareas</h1>
    <input class="textInput" v-model="tarea" type="text" name id />
    <!-- Con el botón llamo a la función agregar, para agregar una tarea mediante el evento click-->
    <button class="boton" @click="agregar">Agregar Tarea</button>
    <!-- Título lista de tareas -->
    <h5 class="títuloLista">Cosas por hacer:</h5>
    <!-- LLamado al componente tarea, uso de directiva v-for para recorrer el arreglo tareas, y llamado al evento eliminar, para eliminar una tarea -->
    <tarea
      v-for="(tarea, i) in tareas"
      :tarea="tarea"
      :indice="i"
      :key="i"
      @eliminar="eliminar"
    ></tarea>
  </div>
</template>

<script>
// Importo componente hijo tarea
import tarea from "./components/Tarea";
export default {
  // Nombre del componente
  nombre: "listaTareas",
  // Función data retorna un string vacío en que se guardan los datos ingresados en el input
  // y un array vacío donde se guardan en conjunto los strings, ingresados.
  data() {
    return {
      tarea: "",
      tareas: [],
    };
  },
  // Referencia al componente hijo "tarea"
  components: {
    tarea,
  },
  // Métodos
  methods: {
    // Función "agregar", mediante el método push, ingreso el string tarea, al array tareas
    agregar() {
      this.tareas.push(this.tarea);
      this.tarea = "";
    },
    // Mediante el método splice elimino un objeto (en este caso una tarea), del array tareas
    eliminar(indice) {
      this.tareas.splice(indice, 1);
    },
  },
};
</script>

<style></style>
