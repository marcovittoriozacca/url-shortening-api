<script setup>
import CyanButton from './CyanButton.vue';
import { store } from '../../store.js'
import { ref } from 'vue';
import axios from 'axios';
const apiUrl = 'https://cleanuri.com/api/v1/shorten';

let userLink = ref('');

async function shortenLink(){
    const endpoint = {
        url: encodeURIComponent(userLink.value),
    };

    await axios.post(apiUrl, endpoint).then((res) => console.log(res));
}


</script>

<template>

    <div class="flex flex-col gap-y-5">

        <div class="violet-banner rounded-md m-5">
            <div class="flex flex-col gap-y-8 p-6">
                <input v-model="userLink" class="w-full py-3 px-5 focus:outline-none focus:ring focus:ring-[#2acfcf] rounded" type="text" name="url" id="url" placeholder="Shorten a link here...">
                <!-- <small>Please add a link here</small> -->
                <CyanButton
                    text = 'Shorten it!'
                    :animation = true
                    class="rounded"

                    @click="shortenLink"
                />
            </div>
        </div>

        <div v-for="(link, index) in store.shortenedLinks" :key="index">
            
        </div>
    </div>

    
</template>

<style lang="scss" scoped>
@use '../../style/scss/general' as *;

.violet-banner{
    background-image: url('/images/bg-shorten-mobile.svg');
    background-position: top right;
    background-repeat: no-repeat;
    background-size: contain;
    background-color: $dark-violet;
}


</style>