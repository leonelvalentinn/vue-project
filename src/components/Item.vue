<script setup>
  import { inject } from 'vue'
  const props = defineProps({
    index: Number,
    ropa: String,
    marca: String,
    nota: Number
  })

  const stuff = inject('clothes')

  const handleChangeRate = () => {
    if (props.nota <= 5) {
      stuff.value[props.index].nota += 1
    } else {
      stuff.value[props.index].nota = 1
    }
    
  }
</script>

<template>
  <article class='item'>
    <p><strong>{{ ropa }}</strong> {{ marca }}</p>
    <div>
      <img v-if='nota >= 1' src='https://www.html6.es/img/estrella.png' alt='Estrella'>
      <img v-if='nota >= 2' src='https://www.html6.es/img/estrella.png' alt='Estrella'>
      <img v-if='nota >= 3' src='https://www.html6.es/img/estrella.png' alt='Estrella'>
      <img v-if='nota >= 4' src='https://www.html6.es/img/estrella.png' alt='Estrella'>
      <img v-if='nota >= 5' src='https://www.html6.es/img/estrella.png' alt='Estrella'>
      <img v-if='nota === 6' src='https://www.html6.es/img/estrella.png' alt='Estrella'>
    </div>
    <button class='btn' @click='handleChangeRate'>+</button>
  </article>
</template>

<style scoped>
  .item {
    width: 100%;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  div {
    width: 180px;
    display: flex;
    justify-content: flex-start;
  }
  img {
    width: 30px;
  }
  p {
    padding: 5px 10px;
    background-color: aliceblue;
    border-radius: 10px;
    color: #2f2f2f;
  }
  .btn {
    text-align: center;
  }
</style>