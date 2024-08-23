<script setup lang="ts">
import LightBoxGallery from './components/LightBoxGallery.vue'

const images = [
  'https://picsum.photos/200/300',
  'https://picsum.photos/200',
  'https://picsum.photos/300',
  'https://picsum.photos/300/400',
  'https://picsum.photos/400'
];
</script>

<template>
  <header>

  </header>

  <main>
    <LightBoxGallery :images />
  </main>
</template>

<style scoped>

</style>
