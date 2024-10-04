<script setup>
import CardKing from './CardKing.vue'
import { productos } from '../datos'
import { ref } from 'vue'

const numberOfKing = ref(0)

const handleNextKing = () => {
  if (numberOfKing.value < productos.length - 1) {
    numberOfKing.value++
  } else {
    numberOfKing.value = 0
  }
}
</script>

<template class='container'>
  <div class='div'>
    <CardKing :id='numberOfKing' :kings='productos[numberOfKing]' :numberOfKings='productos.length' />
    <button @click='handleNextKing'>Siguiente (<span>{{ numberOfKing + 1 }}</span>/{{ productos.length }})</button>
  </div>
</template>

<style scoped>
  .container {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    max-width: 650px;
  }

  .div {
    border: 1px white solid;
    border-radius: 8px;
    padding: 1rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>