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
  'https://picsum.photos/2000/1200',
  'https://picsum.photos/1800/1200'
];
</script>

<template>
  <header>
    <h1>Vue Lightbox Gallery</h1>
  </header>

  <main>
    <LightboxGallery :images />
  </main>
</template>

<style scoped>
header {
  padding: 15px 30px;
  border-bottom: 4px solid black;
}

main {
  padding-top: 15px;
}
</style>
