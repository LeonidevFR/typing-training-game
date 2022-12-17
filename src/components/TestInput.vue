<template>
  <div class="w-auto text-4xl font-medium pl-4">
    <span
      v-for="(item, index) in reference.replaceAll(' ', '`').split('')"
      :key="index"
      :class="getFontColor(item, index)"
    >
      {{ item === "`" ? "&nbsp" : item }}
    </span>
  </div>
  <input type="text" v-model="input" />
</template>

<script setup>
import { ref, watch } from "vue";

const reference = ref("The quick brown fox plays in the meadow");
const input = ref("");

watch(input, (newVal, oldVal) => {
  let length = newVal.length;

  console.log(reference.value[length - 1]);
});

const getFontColor = (item, index) => {
  if (input.value.length >= index + 1) {
    if (input.value[index] === item) {
      return "text-teal-500";
    } else {
      return "text-red-500";
    }
  }
};
</script>
