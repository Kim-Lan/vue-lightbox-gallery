<script setup lang="ts">
import LightboxGallery from './components/LightboxGallery.vue'

const images = [
  'https://picsum.photos/200/300',
  'https://picsum.photos/200',
  'https://picsum.photos/2000/1500',
  'https://picsum.photos/2000/1000',
  'https://picsum.photos/1000'
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
