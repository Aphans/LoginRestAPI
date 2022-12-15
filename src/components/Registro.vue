<template>
      <FormRegister @enviarDatos="registrarUsuario"/>
  </template>
  <script setup>
  import {ref} from "vue";
  import axios from "axios";
  import FormRegister from "./FormRegister.vue";
  const registrarUsuario = async(datos) => {
    try {
      const response = await axios.post(`http://localhost:3000/usuarios/`,{
        usuario:datos.usuario,
      });
    } catch(error) {
      console.log("No hemos podido registrar al usuario");
    }
  }
  </script>
  <style scoped>
  </style>