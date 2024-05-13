<script setup>
  import NavBar from './components/header/NavBar.vue';
  import HomePage from './pages/HomePage.vue';
  import { store } from './store';
  import { onMounted} from 'vue';

onMounted(() => {
  console.log(localStorage)
  if(localStorage.getItem('previousLink') !== null){
    store.shortenedLinks = JSON.parse(localStorage.getItem('previousLink'));
  }  
})


</script>

<template>
  
  <NavBar class="z-50"/>

  <!-- pages -->
  <HomePage/>
  

</template>

<style scoped lang="scss">

</style>
