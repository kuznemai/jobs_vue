<script setup lang="ts">
defineProps<{
  src: string;
  alt?: string;
  reviewLink?: string; // 🔥 ссылка на отзыв
}>();
</script>

<template>
  <div class="slider__element">
    <div class="image-wrapper">
      <img :src="src" :alt="alt || 'slider image'" />
      <slot name="overlay"></slot>
    </div>
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

.image-wrapper {
  position: relative;
  width: 100%;
}

.image-wrapper img {
  width: 100%;
  height: auto;
  border-radius: 12px; /* опционально */
}

::v-deep([slot="overlay"]) {
  position: absolute;
  bottom: 10px; /* можно top/left/right — как нужно */
  right: 10px;
  z-index: 5;
}

@media (max-width: 768px) {
  .slider__element {
    flex: 0 0 70%;
  }
}
</style>
