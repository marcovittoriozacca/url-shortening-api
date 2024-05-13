<script setup>
import CyanButton from '../main/CyanButton.vue';
import { onMounted, ref } from 'vue';

 //variables
let burgerClicked = ref(false);
const menuLink = [
    {
        name: 'features',
        path: '#',
        active: false,
    },
    {
        name: 'pricing',
        path: '#',
        active: false,
    },
    {
        name: 'resources',
        path: '#',
        active: false,
    },
]

//functions
const openBurgerMenu = () =>{
    burgerClicked.value = !burgerClicked.value;
}

//onMounted functions
onMounted( () => {
    burgerClicked.value = false;
})
</script>

<template>

<header class="bg-white fixed top-0 w-full">
    <nav class="nav-bar px-5 sm:px-0 relative z-50">
        <div class="flex items-center justify-between bg-white pt-8 pb-6">
            <ul class="h-full">
                <li>
                    <img src="/images/logo.svg" alt="das">
                </li>                
            </ul>

            <ul class="h-full">
                <li>
                    <button @click="openBurgerMenu" class="transition-transform linear active:scale-110">
                        <i class="fas fa-bars text-slate-400 text-2xl"></i>
                    </button>
                </li>
            </ul>
        </div>

        
        <!-- burger menu -->
        <div class="absolute left-0 right-0 mx-5 sm:mx-0 pt-5 transition-all duration-[400ms] ease-out z-[-1]" :class="[burgerClicked ? 'top-[68px]' : 'top-[-385px]']">
            <ul class="font-bold text-neutral-50 text-center burger-menu-bg rounded-xl py-10 px-10">
                <li v-for="link in menuLink" class="mb-7">
                    <a :href="link.path">
                        <h4 class="capitalize hover:text-[#2acfcf] transition-colors duration-200">{{ link.name }}</h4>
                    </a>
                </li>
                <hr class="mb-7 border-slate-400/50 border-t-[.5px]">
                <div class="flex flex-col gap-y-7">
                    <a href="#" class="hover:text-[#2acfcf] transition-colors duration-200">Login</a>
                    <a href="#">
                        <CyanButton
                            link = '#'
                            text = 'Sign Up'
                            :animation = true
                        />
                    </a>
                </div>
            </ul>
        </div>
    </nav>

</header>

</template>

<style lang="scss" scoped>
@use '../../style/scss/general' as *;

.burger-menu-bg{
    background-color: $dark-violet;
}

.cyan-btn{
    background-color: $cyan;
}

</style>