<script setup lang="ts">
import { ref, computed } from 'vue'

export interface Props {
  images: string[]
  maxSize?: number
}

const props = withDefaults(defineProps<Props>(), {
  maxSize: 300
});

const maxSizeString = computed(() => props.maxSize + 'px');

const isLightboxVisible = ref(false);
const currentImage = ref('');

function showLightbox(index: number) {
  isLightboxVisible.value = true;
  currentImage.value = props.images[index];
}

function closeLightbox() {
  isLightboxVisible.value = false;
  currentImage.value = '';
}
</script>

<template>
  <div class="gallery">
    <div
      v-for="(image, index) in props.images"
      class="gallery-image"
      @click="showLightbox(index)"
    >
      <img :src="image" />
    </div>
  </div>

  <div
    v-if="isLightboxVisible"
    class="lightbox"
    @click.self="closeLightbox"
  >
    <img :src="currentImage" />
  </div>
</template>

<style scoped>
.gallery {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  gap: 5px;
  margin: 5px;
}

.gallery-image {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
  flex-shrink: 1;
  max-width: v-bind(maxSizeString);
  cursor: pointer;
}

.gallery-image img {
  display: block;
  object-fit: cover;
  flex-grow: 1;
  flex-shrink: 1;
  max-height: v-bind(maxSizeString);
  border-radius: 5px;
}

.lightbox {
  position: fixed;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(10, 10, 10, 0.85);
  z-index: 1000;
}
</style>
