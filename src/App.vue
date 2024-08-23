<script setup lang="ts">
import LightboxGallery from './components/LightboxGallery.vue'

const images = [
  'https://picsum.photos/600/800',
  'https://picsum.photos/600',
  'https://picsum.photos/2000/1500',
  'https://picsum.photos/2000/1000',
  'https://picsum.photos/1000',
  'https://picsum.photos/1920/1080',
  'https://picsum.photos/1280/720',
  'https://picsum.photos/2000/1200'
];
</script>

<template>
  <header>

  </header>

  <main>
    <LightboxGallery :images />
  </main>
</template>

<style scoped>

</style>
