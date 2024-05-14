<script setup>
import { defineProps } from "vue";

defineProps({
  text: String,
  animation: Boolean,
  copied: Boolean,
});
</script>

<template>
  <button v-if="copied" class="violet-btn rounded-full">Copied!</button>

  <button
    v-else
    class="cyan-btn rounded-full"
    :class="{ animation: animation }"
  >
    {{ text }}
  </button>
</template>

<style lang="scss" scoped>
@use "../../style/scss/general" as *;

button {
  @apply w-full py-[15px] font-bold text-white;
}

.cyan-btn {
  background-color: $cyan;
  &:hover {
    background-color: #9be3e2;
  }
}
.violet-btn {
  background-color: $dark-violet;
}

.animation {
  @apply transition-transform duration-200 hover:scale-[103%] active:scale-100;
}
</style>
