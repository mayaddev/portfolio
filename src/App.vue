<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import MainNav from "./components/MainNav.vue"
import Footer from './components/Footer.vue';
</script>

<template>

    <MainNav></MainNav>
    <RouterView />
    <Footer></Footer>
</template>

<style scoped>
/* في ملف CSS */
footer a {
  position: relative;
}
footer a::after {
  content: '';
  position: absolute;
  width: 0;
  height: 2px;
  bottom: -2px;
  left: 0;
  background-color: #f59e0b;
  transition: width 0.3s ease;
}
footer a:hover::after {
  width: 100%;
}
</style>
