<script setup>
import { defineProps } from "vue";
const props = defineProps({
  title: String,
  paragraph: String,
  titleSize: String,
});

const setFontSize = () => {
  switch (true) {
    case props.titleSize != undefined:
      return props.titleSize;
    default:
      return "text-3xl";
  }
};
</script>

<template>
  <div>
    <h2 :class="setFontSize()" class="title">{{ title }}</h2>
    <p class="paragraph">{{ paragraph }}</p>
  </div>
</template>

<style lang="scss" scoped>
@use "../../style/scss/general" as *;
.title {
  @apply mb-4 font-extrabold;
  color: $very-dark-blue;
}
.paragraph {
  @apply text-slate-400;
}
</style>
