<script setup>
import { computed, ref } from 'vue';

const contador1 = ref(0);
const contador2 = ref(0);
const valorBooleano = ref(true);

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
   <h1>Exercício Propriedades Computadas</h1>
  <div class="booleano">
    <button @click="valorBooleano = !valorBooleano">
       {{ valorBooleano ? 'Esconder Resultado' : 'Mostrar Resultado' }}
      
    </button>
  </div>
  <div v-if="valorBooleano">
  <div class="contadores">
    <h2>contador 1</h2>
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
</div>
</template>

<style scoped>
.contadores {
  padding: 20px 30px;
  background-color: white;
  color: rgb(10, 10, 10);
  border-radius: 10px;
  text-align: center;
  margin: 30px;
}

h1{
  color: rgb(12, 139, 0);
  font-weight: bold;
  font-size: 3rem;
  margin: 10px;
  text-align: center;
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
  background-color: rgb(0, 255, 26);
}

div {
  padding: 10px;
  border-radius: 5px;
  color: rgb(27, 25, 25);
  font-weight: bold;
}
.booleano {
  text-align: center;
}
.soma {
  text-align: center;
  background-color: white;
  padding: 20px 30px;
  margin: 30px
}
</style>
