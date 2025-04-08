<script setup>
import { computed, ref } from 'vue';

const contador1 = ref(0);
const contador2 = ref(0);

function incrementar1() {
  contador1.value++;
}
function decrementar1() {
  contador1.value--;
}
function incrementar2() {
  contador2.value++;
}
function decrementar2() {
  contador2.value--;
}

const soma = computed(() => contador1.value + contador2.value);
const somaPar = computed(() => soma.value % 2 === 0);
const somaMaiorQue10 = computed(() => soma.value > 10);
</script>

<template>
  <div class="contadores">
    <h1>contador 1</h1>
    <p>Valor: {{ contador1 }} </p>
    <button @click="incrementar1">+</button>
    <button @click="decrementar1">-</button>
    <hr />
    <h2>contador 2</h2>
    <p>Valor: {{ contador2 }}</p>
    <button @click="incrementar2">+</button>
    <button @click="decrementar2">-</button>
  </div>
  <div class="soma">
    <h2>Soma</h2>
    <p>Valor: {{ soma }} </p>
    <div v-if="somaMaiorQue10" :style="{ backgroundColor:'green'}">
      <p>A soma é maior que 10</p>
    </div>
    <div v-else :style="{backgroundColor:'red'}">
      <p>A soma é menor que 10</p>
    </div>
    <div v-if="somaPar">
      <p>A soma é par</p>
    </div>
    <div v-else>
      <p>A soma é ímpar</p>
    </div>
  </div>
</template>

<style scoped>
.div {
  margin: 10px 0;
  padding: 10px;
  border-radius: 5px;
  color: rgb(27, 25, 25);
  font-weight: bold;
}
button {
  margin: 10px;
  padding: 10px;
  border: 0;
  border-radius: 5px;
  background-color: rgb(139, 224, 143);
  color: black;
  font-weight: bold;
  cursor: pointer;
}
button:hover {
  background-color: azure;
}
</style>
