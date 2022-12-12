<template>
    <div v-for="el in usuario" v-bind:key="el.id">
        {{el.usuario}}
    </div>
</template>
<script setup>
import {ref,computed,onMounted} from "vue";
import axios from "axios";
const usuario = ref([]);
onMounted(()=>{
    obtenerUsuario();
})
const obtenerUsuario = async()=>{
    try{
    const response = await axios.get('http://localhost:3000/usuarios?usuario=Pepe&contraseña=hello');
    console.log(response);
    usuario.value = response.data;
    }catch(error){
        console.log("No se ha obtenido el usuario");
    }
  }
</script>
<style scoped>
</style>