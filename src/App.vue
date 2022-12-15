<template>
  <button @click="showRegister=true,showLogin=false">Registro</button>
  <button @click="showLogin=true,showRegister=false">Login</button>
  <div v-if="showRegister">
    <Registro/>
  </div>
  <div v-if="showLogin">
    <Login/>
  </div>
</template>
<script setup>
import {ref} from "vue";
import Registro from "@/components/Registro.vue";
import Login from "./components/Login.vue";
const showRegister=ref(false);
const showLogin=ref(false);
</script>
<style setup>
</style>