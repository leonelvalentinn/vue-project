<script setup>
  import { ref } from 'vue'
import Child from './Child.vue';

  const name = ref('Leonel')
  const age = ref(27)
</script>

<template>
  <h1>Padre</h1>
  <Child :name='name' :age='age' />
</template>

<style>

</style>