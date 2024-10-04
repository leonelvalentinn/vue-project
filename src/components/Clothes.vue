<script setup>
  import { stuff } from '../mocks/datos.js'
  import Item from './Item.vue'
  import { provide } from 'vue'

  provide('clothes', stuff)
</script>

<template>
  <div class='container' v-for='(item, index) in stuff' :key="index">
    <Item :ropa='item.ropa' :marca='item.marca' :nota='item.nota' :index='index' />
  </div>
</template>

<style scoped>
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    padding: 1rem;
    border: 1px rgba(128, 128, 128, 0.7) solid;
    border-radius: 10px;
    gap: 10px;
  }
</style>