<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps<{
  images: string[]
}>();

const visible = ref(false);
const index = ref(0);
</script>

<template>
  <div>
    <img v-if="visible" :src="props.images[index]" />
  </div>
</template>

<style scoped>

</style>
