<template>
      <FormRegister @enviarRegistro="registrarUsuario"/>
  </template>
  <script setup>
  import {ref} from "vue";
  import axios from "axios";
  import FormRegister from "./FormRegister.vue";
  const registrarUsuario = async(datos) => {
    try {
      const response = await axios.post(`http://localhost:3000/usuarios/`,{
        usuario:datos.usuario,
        contraseña:datos.contraseña,
        nivel:datos.nivel,
      });
    } catch(error) {
      console.log("No hemos podido registrar al usuario");
    }
  }
  </script>
  <style scoped>
  </style>