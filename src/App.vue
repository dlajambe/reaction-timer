<script setup lang="ts">
import Block from './components/Block.vue';
import { ref } from 'vue'

let isPlaying:boolean = false;
const delay = ref();
const timeTaken = ref();
// let startTime = performance.now();

function startGame() {
  isPlaying = true;
  delay.value = Math.random()*(7 - 2) + 2;
  console.log(delay.value);
  startTime = performance.now()
}

function stopTimer() {
  timeTaken.value = performance.now() - startTime;
  isPlaying = false;
  console.log(timeTaken.value)
}

</script>

<template>
  <h1>
    Ninja Reaction Timer
  </h1>
  <p>{{ delay }}</p>
  <button @click="startGame">Play</button>
  <Block @click="stopTimer"/>
  <
</template>
<style>

</style>
