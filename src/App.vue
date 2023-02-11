<script setup lang="ts">
import { RouterView } from 'vue-router'
import FooterMenu from '@/components/FooterMenu.vue'
import HeaderMenu from './components/HeaderMenu.vue';
</script>

<template>
  <div class="wrapper">
    <header>
      <HeaderMenu></HeaderMenu>
    </header>

    <section>
      <RouterView />
    </section>
  </div>
  <footer class="footer">
    <FooterMenu></FooterMenu>
  </footer>
</template>

<style scoped>
.wrapper {
  min-height: 100%;
  margin-bottom: -50px;
}

.title {
  padding-top: 5.5em;
  text-align: center;
  color: #fff8e4;
  font-size: 2.1em;
  font-family: 'Arial Black', Arial, sans-serif;
  font-weight: 900;
  font-style: normal;
  text-shadow: 1px 1px 4px #4f4732;
}

.footer,
.push {
  height: 50px;
}
</style>
