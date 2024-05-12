<script setup>
import { defineProps } from 'vue';

defineProps({
    link: String,
    text: String,
    animation: Boolean,
});
</script>

<template>
    <button class="w-full cyan-btn rounded-full py-3" :class="{'hover:scale-105 transition-transform duration-200' : animation}">{{ text }}</button>
</template>

<style lang="scss" scoped>
@use '../../style/scss/general' as *;

.cyan-btn{
    background-color: $cyan;
}
</style>