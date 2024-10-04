<script setup lang="ts">
import {ref} from 'vue'
import type { Game } from '../types/Game';

const props = defineProps<{
    games: Game[]
}>();

let bestGameId: number = 0;
let bestGameReactionTime: number = Infinity;

for (const game of props.games) {
    if (game.reactionTime < bestGameReactionTime) {
        bestGameReactionTime = game.reactionTime;
        bestGameId = game.gameId;
    }
}
</script>

<template>
    <div>
        <p v-for="game in props.games" :class="{bestGame: game.gameId == bestGameId}">
            Game {{ game.gameId }}: {{ game.reactionTime }} ms
        </p>
    </div>
</template>

<style>
.bestGame {
    font-weight: bold;
}
</style>