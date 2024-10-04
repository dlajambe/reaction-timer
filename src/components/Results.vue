<script setup lang="ts">
import {ref} from 'vue'
const props = defineProps<{
    gameNumber: number,
    reactionTime: number
}>();
</script>

<template>
  <p>Game {{ props.gameNumber }}: {{ props.reactionTime }} ms</p>
</template>