<script setup lang="ts">
import { RouterView } from 'vue-router'
import FooterMenu from '@/components/FooterMenu.vue'

</script>

<template>
  <header>
    <div class="title">
      <h1>Radio Lost Cause<span class="beta">β</span></h1>
    </div>
  </header>
  <RouterView />
  <footer>
    <FooterMenu></FooterMenu>
  </footer>
</template>

<style scoped>
.title {
  padding-top: 5.5em;
  text-align: center;
  color: #fff8e4;
  font-size: 2.1em;
  font-family: auto-pro-small-caps, sans-serif;
  font-weight: 900;
  font-style: normal;
  text-shadow: 1px 1px 4px #4f4732;
}

.beta {
  font-size: 0.5em;
  font-weight: 400;
  vertical-align: sub;
}
</style>
