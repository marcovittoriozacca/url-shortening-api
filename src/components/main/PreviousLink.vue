<script setup>
import CyanButton from './CyanButton.vue';
import {ref, defineProps, onMounted, watch} from 'vue';
import { useClipboard } from '@vueuse/core'

//props
const props = defineProps({
    longLink: String,
    shortLink: String,
});

//variables
const linkToCopy = ref(props.shortLink);
const { text, copy, copied, isSupported } = useClipboard({ linkToCopy });

//onMounted
onMounted(() => {
    linkToCopy.value = props.shortLink;
});


watch(() => props.shortLink, (newValue) => {
    linkToCopy.value = newValue;
});



</script>

<template>
    <div class="bg-white m-5 sm:m-0 sm:mt-5 max-w-[640px] rounded-md general-container-lg-class">
        <!-- long link -->
        <div class="p-3 font-semibold text-very-dark-blu lg:w-1/2">
            <h3>{{ longLink }}</h3>
        </div>

        <hr class="lg:hidden">

        <!-- short link -->
        <div class="p-3 lg:flex lg:items-center lg:gap-x-3 lg:w-1/2 lg:justify-end">
            <h3 class="py-3 short-link">{{ shortLink }}</h3>
            <div v-if="isSupported" class="lg:w-1/6">
                <CyanButton
                    text = 'Copy'
                    :animation = true
                    class="rounded-md "
                    :copied = copied
                    @click="copy(linkToCopy)"
                />
            </div>
        </div>
    </div>
</template>



<style lang="scss" scoped>
    @use '../../style/scss/general' as *;
    .short-link{
        @apply py-3 font-semibold;
        color: $cyan;
    }

    .text-very-dark-blue{
    color: $very-dark-blue;
}
.general-container-lg-class{
    @apply lg:container lg:flex lg:items-center lg:justify-between lg:mb-5;
}

</style>