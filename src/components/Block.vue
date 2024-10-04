<script setup lang="ts">
import {ref, onMounted} from 'vue'

const props = defineProps<{
  delay?: number
}>();

const emit = defineEmits<{
  endGame: [reactionTime: number]
}>();

const showBlock = ref(false);
let startTime: number = 0;
let reactionTime: number = 0;

onMounted(() => {
  console.log("Block mounted");
  console.log("Block delay: " + props.delay);
  setTimeout(() => {
    showBlock.value = true;
    startTime = performance.now();
  }, props.delay);
})

function stopTimer() {
  console.log("Timer stopped");
  reactionTime = performance.now() - startTime;
  emit('endGame', reactionTime);
}
</script>

<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click me!
  </div>
</template>

<style>

.block {
    width: 400px;
    height: 200px;
    border-radius: 20px;
    background-color: aqua;
    display: flex;
    flex-direction: column;
    justify-content: center;
}

</style>