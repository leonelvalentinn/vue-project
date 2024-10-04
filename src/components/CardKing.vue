<script setup>
import { computed } from 'vue'

  const imgSrc = 'oferta.jpg'

  defineProps({
    id: Number,
    kings: Array,
    numberOfKings: Number
  })

  const getURIImg = (name) => {
    const lowerName = name.toLocaleLowerCase()
    const uri = `https://www.html6.es/img/rey_${lowerName}.png`
    return uri
  }

  const getPriceOff = (price) => {
    const discount = price * 0.9
    const priceOff = Number(discount.toFixed(2))

    return priceOff
  }
</script>

<template>
  <article class='card'>
    <h1>Cena {{ id + 1 }} con el rey godo <span>{{ kings.nombre }}</span></h1>
    <p>Precio: <span>${{ kings.precio }}</span></p>
    <small :class='kings.finDeSemana && "weekend"'>{{ kings.finDeSemana ? '(Sólo fines de semana)' : '(De lunes a domingo)' }}</small>
    <div class='off' v-show='kings.precio < 100'>
      <p>Ahorra un 10% dto: <span>${{ getPriceOff(kings.precio) }}</span></p>
      <img class='sale' :src='imgSrc' alt='Etiqueta de oferta'>
    </div>
    <img class='king-img' :src='getURIImg(kings.nombre)' alt='Imagen del rey'>
  </article>
</template>

<style scoped>
  .card {
    padding: 1rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    & h1 {
      font-weight: 600;
      font-size: 2rem;
      margin-top: 0;
    }

    & span {
      color: greenyellow;
    }

    & small {
      background-color: greenyellow;
      padding: 5px 8px;
      border-radius: 8px;
      color: rgb(41, 41, 41);
    }

    & .weekend {
      background-color: tomato;
    }

    & .off {
      display: flex;
      align-items: center;
      gap: 10px;

      & .sale {
        width: 60px;
        height: auto;
      }
    }

    & button {
      margin-top: 1rem;

      & span {
        color: white;
      }
    }

    & .king-img {
      margin-top: 16px;
    }

  }
</style>