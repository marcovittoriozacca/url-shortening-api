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
    <div class="border border-gray-200 m-5 sm:m-0 sm:mt-5 max-w-[640px] mx-auto rounded-md">
        <!-- long link -->
        <div class="p-3 font-semibold text-very-dark-blue">
            <h3>{{ longLink }}</h3>
        </div>

        <hr>

        <!-- short link -->
        <div class="p-3">
            <h3 class="py-3 short-link">{{ shortLink }}</h3>
            <div v-if="isSupported">
                <CyanButton
                    text = 'Copy'
                    :animation = true
                    class="rounded"
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

</style>