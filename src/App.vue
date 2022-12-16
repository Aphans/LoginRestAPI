<template>
  <FormLogin @enviarView="viewRecibida"/>
  <div v-if="view">
    <Login/>
  </div>
  <div v-else>
    <FormRegister/>
  </div>
</template>
<script setup>
import {ref} from "vue";
import FormLogin from "@/components/FormLogin.vue";
import FormRegister from "@/components/FormRegister.vue";
import Login from "@/components/Login.vue";
const view = ref(false);
const viewRecibida = (data) =>{
  console.log(data);
  view.value=data;
}
</script>
<style setup>
</style>