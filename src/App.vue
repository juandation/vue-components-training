<script setup>
import IdCard from './components/IdCard.vue'
</script>

<template>
  <h1>Creación de componentes con Vue</h1>
  <p>Crea a continuación todos los componentes del ejercicio.</p>
  
  <!-- Example 1: Using v-bind syntax for non-string props -->
  <IdCard
    first-name="John"
    last-name="Doe"
    gender="male"
    :height="180"
    :birth="new Date('1990-05-15')"
    picture="/maxence.png"
  />
  
  <!-- Example 2: Using v-bind syntax with different data -->
  <IdCard
    first-name="Jane"
    last-name="Smith"
    gender="female"
    :height="165"
    :birth="new Date('1985-12-03')"
    picture="/maxence-glasses.png"
  />
  
  <!-- Example 3: Testing with string literals where possible -->
  <IdCard
    first-name="Alice"
    last-name="Johnson"
    gender="female"
    :height="172"
    :birth="new Date('1992-07-20')"
    picture="/maxence.png"
  />
</template>

<style scoped>

</style>
