<template>
  <input
    type="text"
    placeholder="The quick brown fox plays in the meadow"
    v-model="userInput"
  />
</template>

<script setup>
import { ref } from "vue";

const userInput = ref("");
</script>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
