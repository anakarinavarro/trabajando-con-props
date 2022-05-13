<template>
  <div class="container">
    <div class="row justify-content-md-center">
      <div class="col-6">
        <h1 class="titulo">Lista de tareas</h1>
        <form class="formulario" @submit.prevent="agregarTarea">
          <div class="form-group d-flex">
            <input
              v-model="nuevaTareaAgregada"
              type="text"
              class="form-control"
              placeholder="Ingresa una tarea"
            />
            <button type="submit" class="btn btn-primary">Agregar</button>
          </div>
          <h3 class="listado">Lista de tareas:</h3>
          <ul>
          <NuevaTarea
          v-for="(tarea, index) of tareas"
          @tareaLista="borrarTarea($emit)"
          :key="index"
          :indexTarea="index"
          :tareaAgregada="tarea"
          />
          </ul>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import NuevaTarea from '@/components/NuevaTarea.vue'
export default {
  name: "App",
  data: ()=>({
    nuevaTareaAgregada: "",
    tareas: [],
   
  }),
  components: {
    NuevaTarea
  },
  methods: {
    agregarTarea(){
      this.tareas.unshift(this.nuevaTareaAgregada)
      this.nuevaTareaAgregada = ""
    },
    borrarTarea(key){
      this.tareas.splice(key, 1)
    }
  }
  
};
</script>

<style>
.titulo {
  text-align: center;
  padding-bottom: 10px;
  margin-bottom: 10px;
}
.listado{
  text-align: center;
  padding-top: 10px;
  margin-top:  10px;
}
</style>
