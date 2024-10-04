<script setup>
  import { ref, computed } from 'vue' 
  const message = 'Hello World with Vue.js! Pinches perras'
  const myColor = ref('')
  const counter = ref(0)
  const isVisible = ref(true)

  const incrementCounter = () => {
    counter.value++
    if (counter.value > 5) {
      myColor.value = 'verde'
    }
  }

  const check = computed(() => {
    return counter.value === 0
  })
</script>

<template>
  <div class='my-component'>
    <h1 v-if='isVisible'>{{ message }}</h1>
    
    <div>
      <button @click='counter--'>-</button>
      <span :class='myColor'>{{ counter }}</span>
      <button @click='incrementCounter'>+</button>
    </div>
    <div v-if='counter < 0'>Escribe una cantidad mayor a 0</div>
    <div v-else-if='counter > 5'>Escribe una cantidad menor de 5</div>
    <div v-show='check'>No está permitido el número 0</div>

    <button @click='isVisible = !isVisible'>Toggle Visibility</button>
  </div>
</template>

<style>
  .color {
    color: tomato;
  }

  .verde {
    color: greenyellow;
  }
</style>