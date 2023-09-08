<script setup>
import { ref,computed} from 'vue';

const counter = ref(0);
const favoriteNumbers = ref([]);

const increment= () =>{
  counter.value++;
};
const decrease = () => {
  counter.value--;
};
const resetear = () => {
  (counter.value=0);
}

const add = () => {
  favoriteNumbers.value.push(counter.value);
}

const bloquearBtnAdd = computed(() => {
 const numSearch = favoriteNumbers.value.find((num) => num === counter.value);
 return numSearch || numSearch===0;
})
const classCounter = computed(() => {
 if (counter.value==0) {
  return 'zero'
 }
 if (counter.value > 0) {
  return 'positive'
 }
 if (counter.value < 0) {
  return 'negative'
 }
});

</script>

<template>
  <!-- .container -->
<div class="container text-center"> 
    <h1>Hola mundo vue js</h1>
  <h2 @click="saveNumberToList" :class="classCounter" >{{counter}}</h2>
  <div class="btn-group">
    <button class="btn btn-outline-success " @click="increment">Aumentar</button>
    <button class="btn btn-outline-secondary " @click="resetear">Resetear</button>
    <button class="btn btn-outline-danger " @click="decrease">Disminuir</button>
    <button class="btn btn-outline-warning" @click="add" :disabled="bloquearBtnAdd">Add</button>
  </div>
  <ul class="list-group mt-4 p-2">
    <li class="list-group-item" v-for="(num,index) in favoriteNumbers" :key="index">
    {{num}}
    </li>
  </ul>
</div>

</template>

<style>
h1{
  color:aqua;
}
.positive{
  color: green;
}
.negative{
  color: red;
}

</style>