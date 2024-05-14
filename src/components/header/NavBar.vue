<script setup>
import CyanButton from "../main/CyanButton.vue";
import { onMounted, ref } from "vue";

//variables
let burgerClicked = ref(false);
const menuLink = [
  {
    name: "features",
    path: "#",
    active: false,
  },
  {
    name: "pricing",
    path: "#",
    active: false,
  },
  {
    name: "resources",
    path: "#",
    active: false,
  },
];

//functions
const openBurgerMenu = () => {
  burgerClicked.value = !burgerClicked.value;
};

//onMounted functions
onMounted(() => {
  burgerClicked.value = false;
});
</script>

<template>
  <header class="fixed top-0 w-full bg-white">
    <nav class="relative z-50 mx-auto max-w-[640px] px-5 lg:container sm:px-0">
      <div class="flex items-center justify-between bg-white pb-6 pt-8">
        <ul class="h-full lg:flex lg:items-center lg:gap-x-5">
          <li>
            <img src="/images/logo.svg" alt="shortly" />
          </li>
          <li v-for="link in menuLink" class="hidden text-slate-400 lg:block">
            <a :href="link.path">
              <h4
                class="font-semibold capitalize transition-colors duration-200 hover:text-neutral-950"
              >
                {{ link.name }}
              </h4>
            </a>
          </li>
        </ul>

        <ul class="h-full">
          <li>
            <button
              @click="openBurgerMenu"
              class="linear transition-transform active:scale-110 lg:hidden"
            >
              <i class="fas fa-bars text-2xl text-slate-400"></i>
            </button>
            <div class="hidden lg:flex lg:items-center lg:gap-x-6">
              <a
                href="#"
                class="font-semibold text-slate-400 transition-colors duration-200 hover:text-neutral-950"
                >Login</a
              >
              <a href="#">
                <CyanButton
                  link="#"
                  text="Sign Up"
                  :animation="true"
                  class="px-8"
                />
              </a>
            </div>
          </li>
        </ul>
      </div>

      <!-- burger menu -->
      <div
        class="absolute left-0 right-0 z-[-1] mx-5 pt-5 transition-all duration-[400ms] ease-out sm:mx-0 lg:hidden lg:px-5"
        :class="[burgerClicked ? 'top-[68px]' : 'top-[-385px]']"
      >
        <ul
          class="burger-menu-bg rounded-xl px-10 py-10 text-center font-bold text-neutral-50"
        >
          <li v-for="link in menuLink" class="mb-7">
            <a :href="link.path">
              <h4
                class="capitalize transition-colors duration-200 hover:text-[#2acfcf]"
              >
                {{ link.name }}
              </h4>
            </a>
          </li>
          <hr class="mb-7 border-t-[.5px] border-slate-400/50" />
          <div class="flex flex-col gap-y-7">
            <a
              href="#"
              class="transition-colors duration-200 hover:text-[#2acfcf]"
              >Login</a
            >
            <a href="#">
              <CyanButton link="#" text="Sign Up" :animation="true" />
            </a>
          </div>
        </ul>
      </div>
    </nav>
  </header>
</template>

<style lang="scss" scoped>
@use "../../style/scss/general" as *;

.burger-menu-bg {
  background-color: $dark-violet;
}

.cyan-btn {
  background-color: $cyan;
}
</style>
