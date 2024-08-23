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
const currentIndex = ref(0);

function showLightbox(index: number) {
  isLightboxVisible.value = true;
  currentIndex.value = index;
}

function closeLightbox() {
  isLightboxVisible.value = false;
  currentIndex.value = 0;
}

function getPreviousImage() {
  if (currentIndex.value > 0) {
    currentIndex.value -= 1;
  }
}

function getNextImage() {
  if (currentIndex.value < props.images.length - 1) {
    currentIndex.value += 1;
  }
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

  <Transition>
    <div
      v-if="isLightboxVisible"
      class="lightbox"
      @click.self="closeLightbox"
    >
      <!-- Previous Button -->
      <button class="lightbox-button" @click="getPreviousImage">
        <svg
          width="25"
          height="40"
          viewBox="0 0 25 40"
        >
          <polyline
            points="19 5 5 20 19 35"
            stroke-width="3"
            stroke-linecap="butt"
            fill="none"
            stroke-linejoin="round"
            stroke="rgba(255, 255, 255, 0.85)"
          />
        </svg>
      </button>

      <!-- Current Image -->
      <img :src="images[currentIndex]" class="lightbox-content" />

      <!-- Next Button -->
      <button class="lightbox-button" @click="getNextImage">
        <svg
          width="25"
          height="40"
          viewBox="0 0 25 40"
        >
          <polyline
            points="6 5 20 20 6 35"
            stroke-width="3"
            stroke-linecap="butt"
            fill="none"
            stroke-linejoin="round"
            stroke="rgba(255, 255, 255, 0.85)"
          />
        </svg>
      </button>

      <!-- Close Button -->
      <button class="lightbox-button lightbox-close" @click="closeLightbox">
        <svg
          width="30"
          height="30"
        >
          <g
            stroke-width="3"
            stroke="rgba(255, 255, 255, 0.85)"
          >
            <line x1="5" y1="5" x2="25" y2="25" />
            <line x1="5" y1="25" x2="25" y2="5" />
          </g>
        </svg>
      </button>
    </div>
  </Transition>
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

  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 5px;
}

.lightbox-content {
  max-width: 90%;
  max-height: 90%;
}

.lightbox-button {
  background: none;
  border: none;
  padding: 4px;
  
  display: flex;
  justify-content: center;
  align-items: center;

  cursor: pointer;
}

.lightbox-button:hover {
  background: rgb(10, 10, 10, 0.5);
}

.lightbox-close {
  position: absolute;
  top: 5px;
  right: 5px;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
