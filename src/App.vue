<script setup>
  import NavBar from './components/header/NavBar.vue';
  import HomePage from './pages/HomePage.vue';
  import Footer from './components/footer/Footer.vue';
  import { store } from './store';
  import { onMounted} from 'vue';

onMounted(() => {
  if(localStorage.getItem('previousLink') !== null){
    store.shortenedLinks = JSON.parse(localStorage.getItem('previousLink'));
  }  
})


</script>

<template>
  
  <NavBar class="z-50"/>

  <!-- pages -->
  <HomePage/>
  
  <!-- general footer -->
  <Footer/>

</template>

<style scoped lang="scss">

</style>
