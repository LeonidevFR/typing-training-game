<template>
  <div class="relative flex justify-start">
    <input
      id="invisible-input"
      type="text"
      class="w-full h-20 rounded-lg text-4xl font-medium pl-4"
      v-model="inputCharacter"
      autofocus
      @input="handleInput()"
    />
    <div class="w-auto text-4xl font-medium pl-4 absolute top-4">
      <span
        v-for="(item, index) in exercisePhrase.replaceAll(' ', '`').split('')"
        :key="index"
        :class="charIndex > index ? 'text-teal-500' : ''"
      >
        {{ item === "`" ? "&nbsp" : item }}
      </span>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";

const exercisePhrase = ref("The quick brown fox plays in the meadow");
const userInput = ref("");
const inputCharacter = ref("");
const lastInputCharacter = ref("");
const charIndex = ref(0);

watch(userInput, (oldVal, newVal) => {
  if (oldVal !== newVal) {
    let newValLength = newVal.value.length();
    let newchar = newVal.value[newValLength];
    if (newchar === exercisePhrase.value[newValLength]) {
      console.log("FELICITATIONS");
      charIndex.value++;
    }
    inputCharacter.value = "";
  }
});

const handleInput = () => {
  if (inputCharacter.value === exercisePhrase.value[charIndex.value]) {
    console.log("FELICITATIONS");
    charIndex.value++;
  }
  lastInputCharacter.value += inputCharacter.value;
  inputCharacter.value = "";
};
</script>

<style scoped>
#invisible-input {
  /* color: transparent; */
}
</style>
