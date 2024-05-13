<script setup>
import CyanButton from './CyanButton.vue';
</script>

<template>
    <div class="violet-banner">
        <div class="flex flex-col items-center py-24 w-full md:w-1/2 lg:w-1/2 md:mx-auto xl:max-w-[602px]">
        
            <h2 class="mb-5 text-[1.7rem] font-semibold text-white">Boost your links today</h2>
            <div class="w-1/2">
                <CyanButton
                    text = "Get Started"
                    :animation = true
                    
                />
            </div>
            
        </div>
    </div>
</template>

<style lang="scss" scoped>
@use '../../style/scss/general' as *;

.violet-banner{
    background-image: url('/images/bg-boost-mobile.svg');
    background-repeat: no-repeat;
    background-size: cover;
    background-color: $dark-violet;
}

@media screen and (min-width: 1024px){
    .violet-banner{
        background-image: url('/images/bg-boost-desktop.svg');
    }
}
</style>