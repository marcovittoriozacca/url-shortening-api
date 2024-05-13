<script setup>
import SectionText from './SectionText.vue';
import { defineProps } from 'vue';

const props = defineProps({
    obj: Object,
    index: Number
});

const setMarginTop = (id) =>{
    switch (true) {
        case id === 0:
            return 'lg:mt-0';
        case id === 1:
            return 'lg:-mb-20';
        case id === 2:
            return 'lg:-mb-40';    
        default:
            return 'lg:mt-0'
    }
} 

</script>

<template>
    <div v-if="index != 0" class="cyan-bar"></div>
    <div class="card-container relative" :class="setMarginTop(index)">
        <div class="absolute -top-10 lg:left-8">
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
    @apply rounded-md flex flex-col items-center bg-white;
}
.text-container{
    @apply -mt-2 px-7 pt-16 pb-10 sm:pt-20 sm:pb-14 lg:text-start;
}
.cyan-bar{
    @apply h-24 w-3 lg:h-3 lg:w-24;
    background-color: $cyan;

}


</style>