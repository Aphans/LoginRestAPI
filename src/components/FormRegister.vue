<template>
    <div class="flex items-center justify-center h-screen w-full max-w-xs ml-80 mt-50">
      <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
        <div class="mb-4">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
            Username
          </label>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="user" type="text" placeholder="Username" v-model="nombre">
        </div>
        <div class="mb-6">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
            Password
          </label>
          <input class="shadow appearance-none border border-red-500 rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="pass" type="password" placeholder="******************" v-model="contraseña"> 
          <p class="text-red-500 text-xs italic">Please choose a password.</p>
        </div>
        <label class="block text-gray-700 text-sm font-bold mb-2" for="nivel">
            Nivel <select v-model="niveles">
      <option v-for="nivel in niveles" :key="nivel">
        {{ nivel}}
      </option>
    </select>
</label>
<br>
        <div class="flex items-center justify-between">
          <button @click="enviarDatos()" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
            Register
            </button>
        </div>
      </form>
      </div>
    </template>
    <script setup>
    import {ref} from "vue";
    const nombre = ref("");
    const contraseña = ref("");
    const mostrarUsuario = ref(false);
    const niveles = ref([1,2]);
    const emits = defineEmits(['enviarDatos']);
    const enviarDatos = ()=>{
      emits("enviarDatos", {usuario: nombre.value, contraseña:contraseña.value, nivel:niveles.value})
        nombre.value = "";
        contraseña.value = "";
        niveles.value=[];
    }
    </script>