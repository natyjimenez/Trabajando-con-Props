<template>
  <div>
    <!-- LLamado a componente tarea -->
     <ul class="listado">           
            <li> {{tarea}}</li>
        </ul>
    <!-- Botón con un evento click, para borrar una tarea -->
    <button class="btnBorrar" @click="borrar">Eliminar</button>
  </div>
</template>

<script>
// Componente tarea
export default {
  // Nombre del componente
  name: "tarea",
  // Propiedades pasadas de componente padre a componente hijo una de tipo string y otra de tipo number
  props: {
    tarea: String,
    indice: Number,
  },
  // Propiedades pasadas de componente padre a componente hijo
  methods: {
    // Se emite una llamada desde componente hijo con valor eliminar, para ser escuchada por componente padre
    borrar() {
      this.$emit("eliminar", this.indice);
    },
  },
};
</script>

<style></style>
