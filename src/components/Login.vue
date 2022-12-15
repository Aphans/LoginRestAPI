<template>
  <div v-if="!conectado">
    <FormLogin @enviarDatos="obtenerUsuario"/>
  </div>
  <div v-else>
   {{datosUsuario[0].usuario}}
   {{datosUsuario[0].nivel}}
   <button @click="desconectado">Log out</button>
  </div>
</template>
<script setup>
import {ref,onMounted,computed} from "vue";
import axios from "axios";
import FormLogin from "./FormLogin.vue";
const datosUsuario = ref([]);
const show = ref([]);
const desconectar = ref(false);
const obtenerUsuario = async(datos) => {
  try {
    const response = await axios.get(`http://localhost:3000/usuarios?usuario=${datos.usuario}&contraseña=${datos.contraseña}`);
    datosUsuario.value = response.data;
  } catch(error) {
    console.log("No hemos encontrado al usuario");
  }
}
const conectado = computed(() =>{
  return datosUsuario.value.length > 0 } );
const desconectado = computed(()=>{
  return datosUsuario.value.length=0;});
</script>
<style scoped>
</style>