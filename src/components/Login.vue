<template>
    <Form @enviarNombre="nombreRecibido" @enviarContraseña="contraseñaRecibida" @enviarMostrarUsuario="enviarMostrarUsuario"/>
    <div v-for="el in datosUsuario" v-bind:key="el.id">
        {{el.usuario}}
    </div>
</template>
<script setup>
import {ref,onMounted} from "vue";
import axios from "axios";
import Form from "./Form.vue";
const datosUsuario = ref([]);
const usuarioNombre = ref();
const usuarioContraseña = ref();
const mostrarUsuario=ref(false);
onMounted(()=>{
    obtenerUsuario();
})
const obtenerUsuario = async()=>{
    try{
    const response = await axios.get(`http://localhost:8000/usuarios?usuario=${usuarioNombre.value}&contraseña=${usuarioContraseña.value}`);
    console.log(response);
    datosUsuario.value = response.data;
    }catch(error){
        console.log("No se ha obtenido el usuario");
    }
  }
const nombreRecibido = (data)=>{
    usuarioNombre.value = data;
    }
const contraseñaRecibida=(data)=>{
    usuarioContraseña.value=data;
}
const enviarMostrarUsuario=(data)=>{
    mostrarUsuario.value=data;
}
</script>
<style scoped>
</style>