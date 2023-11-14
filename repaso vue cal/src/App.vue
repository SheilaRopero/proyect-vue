<script setup>
import { ref } from 'vue';
let nombreEvento = ref('');
let invitados = ref([
  {nombre: '', apellido:'',fechaNacimiento:'',numeroCelular:'',},
])

const esMenorDeEdad = (fechaNacimiento) => {
  const edad = (fechaNacimiento);
  return edad < 18;
}
</script>

<template>
  <div class="aver">
    <div class=" evento" >
      <h1 class="titulo">Registro de Evento</h1>
      <label class="label" for="nombreEvento">Nombre evento
        <input v-model="nombreEvento" type="text" placeholder="ingrese el nombre de evento">
      </label>

      <div  v-for="(invitado,index) in invitados" :key="index" class="invitado">
      <label class="label" for="Nombre persona">nombre
        <input v-model="invitado.nombre" type="text" placeholder="ingrese  su nombre">
      </label>

      <label class="label" for="apellidos">Apellido
        <input v-model="invitado.apellido" type="text" placeholder="ingrese apellidos">
      </label>

      <label class="label" for="fecha nacimento">Fecha nacimiento
        <input v-model=" invitado.fechaNacimiento  " type="number" id="fechaNacimiento" required placeholder="ingrese su fecha nacimiento">
      </label>

      <label class="label" for="fecha nacimento">Numero de celular
        <input v-model="invitado.numeroCelular" type="number" placeholder="ingrese su celular">
      </label>

      <div>
        <p>nombre del evento : {{ nombreEvento }}</p>
        <p>nombre completo : {{ invitado.nombre }} {{ invitado.apellido }}</p>
        <p>edad : {{ invitado.fechaNacimiento }}</p>
        <p>numero de celular : {{ invitado.numeroCelular }}</p>
        <p v-if=" esMenorDeEdad(invitado.fechaNacimiento) ">requieres acompañante</p>
      </div>

    </div>
  </div>

  </div>
</template>

<style scoped>
.aver {
  font-family: 'Arial', sans-serif;
  background-color: #3508bb;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.invitacion {
  background-color: #fff;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  max-width: 400px;
  width: 100%;
}

.titulo {
  text-align: center;
  color: #333;
}

.evento {
  margin-top: 20px;
}

.label {
  display: block;
  margin-bottom: 10px;
}

input {
  width: 100%;
  padding: 8px;
  margin-top: 4px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

input[type="number"] {
  -moz-appearance: textfield;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>
