<script setup>

import { store } from '../../store.js';
import { ref } from 'vue';
import axios from 'axios';
import validUrl from 'valid-url';

import CyanButton from './CyanButton.vue';

//variables
let userLink = ref('');
let error = ref(false);


//functions
async function shortenUrl(){
    error.value = false;
    let encodedUrl = '';
    
    if(userLink.value === ''){
        error.value = true;
    }
    
    if(validateUrl(userLink.value)){
        encodedUrl = encodeURIComponent(userLink.value);
    }else{
        error.value = true;
    }
    
    if(!error.value){

        try{
            const response = await axios.post(`https://tinyurl.com/api-create.php?url=${encodedUrl}`);
            const lastShortenedLink = response.data;
            error.value = false;

            const newShortLink = {
                longLink: userLink.value,
                shortLink: lastShortenedLink
            }

            store.shortenedLinks.unshift(newShortLink);
            
            localStorage.setItem('previousLink', JSON.stringify(store.shortenedLinks));
            
            userLink.value = ''
        }catch(error){
            console.error(error);
        }

    }
}
function validateUrl(url){
    return validUrl.isUri(url)
}

</script>

<template>
    <div class="violet-banner rounded-md m-5">
        <div class="flex flex-col gap-y-8 p-6">
            <div>
                <input v-model="userLink" class="border-2 w-full py-3 px-5 focus:outline-none focus:ring-2 rounded" :class="[error? 'input-error' : 'input-normal-state']"  type="text" name="url" id="url" placeholder="Shorten a link here...">
                <small class="text-red-500" v-if="error">Please add a link here</small>
            </div>
            <CyanButton
                text = 'Shorten it!'
                :animation = true
                class="rounded"
                @click="shortenUrl"
            />
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

.input-error{
    @apply border-red-500 focus:ring-red-600 bg-rose-100 placeholder-red-600;
}
.input-normal-state{
    @apply focus:ring-[#2acfcf] border-white;
}

</style>