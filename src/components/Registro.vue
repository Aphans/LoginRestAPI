<template>
      <FormRegister @enviarDatos="registrarUsuario"/>
  </template>
  <script setup>
  import {ref} from "vue";
  import axios from "axios";
  import FormRegister from "./FormRegister.vue";
  const registrarUsuario = async(datos) => {
    try {
      const response = await axios.get(`http://localhost:3000/usuarios/`);
      response.data.push(datos);
    } catch(error) {
      console.log("No hemos encontrado al usuario");
    }
  }
  </script>
  <style scoped>
  </style>