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
    <div class="violet-banner rounded-md m-5 sm:m-0 lg:m-0 lg:mb-5">
        <div class="flex flex-col gap-y-9 p-6 lg:flex-row lg:gap-x-7 lg:items-center lg:p-14">
            <div class="flex-1 relative">
                <input v-model="userLink" class="border-2 w-full py-3 px-5 focus:outline-none focus:ring-2 rounded" :class="[error? 'input-error' : 'input-normal-state']"  type="text" name="url" id="url" placeholder="Shorten a link here...">
                <small v-if="error" :class="{'text-red-500 pointer-events-none select-none absolute left-0 -bottom-5 lg:text-lg lg:-bottom-7' : error}" >Please add a link here</small>
            </div>
            <div class="lg:w-1/6">
                <CyanButton
                    text = 'Shorten it!'
                    :animation = true
                    class="rounded-md"
                    @click="shortenUrl"
                />
            </div>
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

@media screen and (min-width : 1024px){
    .violet-banner{
        background-image: url('/images/bg-shorten-desktop.svg');
        background-size: cover;  
    }
}

</style>