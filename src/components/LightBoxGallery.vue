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

const visible = ref(false);
const index = ref(0);
</script>

<template>
  <div class="gallery">
    <div v-for="(image, index) in props.images" class="gallery-image">
      <img :src="image" />
    </div>
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
</style>
