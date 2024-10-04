<script setup lang="ts">
import Block from './components/Block.vue';
import { ref } from 'vue'

const isPlaying = ref(false);
const delay = ref();
const timeTaken = ref();
let gamesPlayed: number = 0;

function startGame() {
  isPlaying.value = true;
  delay.value = Math.random()*(5000 - 2000) + 2000;
  console.log(delay.value);
}

function endGame(reactionTime: number) {
  isPlaying.value = false;
  timeTaken.value = reactionTime;
  gamesPlayed++;
  console.log("Reaction time: " + reactionTime);
  console.log("Games played: " + gamesPlayed);
}

</script>

<template>
  <h1>
    Ninja Reaction Timer
  </h1>
  <button @click="startGame" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" @endGame="endGame" :delay="delay"/>
  <p v-if="!isPlaying && gamesPlayed > 0">Score: {{ timeTaken }}</p>
</template>
<style>

</style>
