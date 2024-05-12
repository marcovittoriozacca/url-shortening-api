<script setup>
import { defineProps } from 'vue';

defineProps({
    text: String,
    animation: Boolean,
    copied: Boolean,
});
</script>

<template>

    <button v-if="copied" class="rounded-full violet-btn " :class="{'animation' : animation}">Copied!</button>

    <button v-else class="rounded-full cyan-btn " :class="{'animation' : animation}">{{ text }}</button>

</template>

<style lang="scss" scoped>
@use '../../style/scss/general' as *;

button{
    @apply w-full py-3 text-white font-bold;
}

.cyan-btn{
    background-color: $cyan;
}
.violet-btn{
    background-color: $dark-violet;
}

.animation{
    @apply hover:scale-105 transition-transform duration-200 active:scale-100;
}
</style>