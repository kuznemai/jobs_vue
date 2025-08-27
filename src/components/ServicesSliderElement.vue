<script setup lang="ts">
defineProps<{
  src: string;
  alt?: string;
}>();
</script>

<template>
  <div class="slider__element">
    <img :src="src" :alt="alt || 'slider image'" />
    <slot name="description"></slot>
  </div>
</template>

<style scoped>
.slider__element {
  flex: 0 0 30%;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px;
  text-align: center;
}

.slider__element img {
  width: 100%;
  height: auto;
}
@media (max-width: 768px) {
  .slider__element {
    flex: 0 0 70%;
  }
}
</style>
