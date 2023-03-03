<template>
  <h1>Practica teachers</h1>
  <p>utilizando manipulacion de objetos y renderiado de ellos con ayuda de reactive y ref 
    al renderizar los elementos y reiniciar el estado debemos hacer push de un elemento nuevo debido a que quedara referenciado es decir hacer un spread o clone 
    si no clonamos tendremos un error de que renderizara espacios en blanco 
  </p>
  <TeacherForm/>
</template>

<script setup> 
import TeacherForm from './components/TeacherForm.vue';
</script>

<style>

</style>
