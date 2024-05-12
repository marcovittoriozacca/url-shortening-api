<script setup>
import { defineProps } from 'vue';

defineProps({
    text: String,
    animation: Boolean,
});
</script>

<template>
    <button class="w-full cyan-btn rounded-full py-3 text-white font-bold" :class="{'hover:scale-105 transition-transform duration-200 active:scale-100' : animation}">{{ text }}</button>
</template>

<style lang="scss" scoped>
@use '../../style/scss/general' as *;

.cyan-btn{
    background-color: $cyan;
}
</style>