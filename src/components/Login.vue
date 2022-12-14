<template>
  <div v-if="!conectado">
    <Form @enviarDatos="obtenerUsuario"/>
  </div>
  <div v-else>
   {{datosUsuario[0].usuario}}
   {{datosUsuario[0].nivel}}
  </div>
</template>
<script setup>
import {ref,onMounted,computed} from "vue";
import axios from "axios";
import Form from "./Form.vue";
const datosUsuario = ref([]);
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
</script>
<style scoped>
</style>