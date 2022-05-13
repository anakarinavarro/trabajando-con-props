<template>
    <li class="componente">
        {{tareaAgregada}}
        <button @click="eliminarTarea" type="button" class="btn btn-danger">Eliminar</button>
    </li>
</template>

<script>
export default{
    name: 'NuevaTarea',
    props: {
        indexTarea : Number,
        tareaAgregada: String

    },
    methods:{
        eliminarTarea(){
        this.$emit("tareaLista", this.indexTarea)
    }
    }
}

</script>

<style>
.componente{
    text-align: center;
  padding-top: 10px;
  margin-top:  10px;
}
</style>