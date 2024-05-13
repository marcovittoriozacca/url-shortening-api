<script setup>
import SectionText from './SectionText.vue';
import { defineProps } from 'vue';

const props = defineProps({
    obj: Object,
    index: Number
});

</script>

<template>
    <div v-if="index != 0" class="cyan-bar"></div>
    <div class="card-container relative">
        <div class="absolute -top-10">
            <figure>
                <img :src="obj.thumb" :alt="obj.title">
            </figure>
        </div>
        <div class="text-container">
            <SectionText
                :title = obj.title
                :paragraph = obj.paragraph
                title-size = 'text-xl'
            />
        </div>
    </div>

</template>

<style lang="scss" scoped>
@use '../../style/scss/general' as *;

figure{
    @apply p-5 rounded-full;
    background-color: $dark-violet;
    img{
        @apply w-11;
    }
}
.card-container{
    @apply rounded-md border flex flex-col items-center;
}
.text-container{
    @apply -mt-2 px-7 pt-16 pb-10 sm:pt-20 sm:pb-14;
}
.cyan-bar{
    @apply h-24 w-3;
    background-color: $cyan;

}


</style>