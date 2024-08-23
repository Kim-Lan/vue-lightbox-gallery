<script setup lang="ts">
import LightBox from './components/LightBox.vue'

const images = [
  'https://picsum.photos/200/300',
  'https://picsum.photos/200',
  'https://picsum.photos/300',
  'https://picsum.photos/300/400'
];
</script>

<template>
  <header>

  </header>

  <main>
    <LightBox :thumbnail="images[0]" :images />
  </main>
</template>

<style scoped>

</style>
