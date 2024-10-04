<script setup lang="ts">
import Block from './components/Block.vue';
import Results from './components/Results.vue';
import { ref } from 'vue';
import type { Game } from './types/Game';

const isPlaying = ref(false);
const delay = ref();
const timeTaken = ref();
const reactionTimes = ref<number[]>([]);
const games = ref<Game[]>([]);

let gamesPlayed: number = 0;

function startGame() {
  isPlaying.value = true;
  delay.value = Math.random()*(5000 - 2000) + 2000;
  console.log(delay.value);
}

function endGame(reactionTime: number) {
  isPlaying.value = false;
  timeTaken.value = reactionTime;
  reactionTimes.value.push(reactionTime);
  gamesPlayed++;

  games.value.push({
    gameId: gamesPlayed,
    reactionTime: reactionTime
  });

  console.log("Reaction time: " + reactionTime);
  console.log("Games played: " + gamesPlayed);
  console.log("Reaction times: " + reactionTimes);
}

</script>

<template>
  <h1>
    Ninja Reaction Timer
  </h1>
  <button @click="startGame" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" @endGame="endGame" :delay="delay"/>
  <Results v-if="!isPlaying && gamesPlayed > 0" :games="games"/>
</template>
<style>

</style>
