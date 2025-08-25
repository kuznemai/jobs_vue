<script setup lang="ts">
import { ref, computed, onMounted, onBeforeUnmount } from "vue";
import RepairPricePopup from "@/components/RepairPricePopup.vue";

type Slide = {
  id?: string | number;
  title: string;
  description: string;
};

const props = withDefaults(
  defineProps<{
    slides: Slide[];
    autoplay?: boolean;
    interval?: number;
  }>(),
  {
    autoplay: false,
    interval: 5000,
  },
);

const current = ref(0);
const total = computed(() => props.slides.length);

function safeIndex(idx: number) {
  return (idx + total.value) % total.value;
}

function next() {
  current.value = safeIndex(current.value + 1);
}
function prev() {
  current.value = safeIndex(current.value - 1);
}
function goTo(i: number) {
  current.value = safeIndex(i);
}

// autoplay
let timer: number | null = null;
function startAutoplay() {
  if (!props.autoplay || total.value <= 1) return;
  stopAutoplay();
  timer = window.setInterval(next, props.interval);
}
function stopAutoplay() {
  if (timer) {
    clearInterval(timer);
    timer = null;
  }
}

// клавиатура
function onKeydown(e: KeyboardEvent) {
  if (e.key === "ArrowRight") next();
  else if (e.key === "ArrowLeft") prev();
}

onMounted(() => {
  window.addEventListener("keydown", onKeydown);
  startAutoplay();
});
onBeforeUnmount(() => {
  window.removeEventListener("keydown", onKeydown);
  stopAutoplay();
});

const isOpen = ref(false);
</script>

<template>
  <RepairPricePopup :isOpen="isOpen" @close="isOpen = false"></RepairPricePopup>

  <diм class="slider" @mouseenter="stopAutoplay" @mouseleave="startAutoplay">
    <div
      class="slides"
      :style="{ transform: `translateX(-${current * 100}%)` }"
    >
      <section
        v-for="(s, i) in slides"
        :key="s.id ?? i"
        class="slide"
        role="group"
        :aria-label="`${i + 1} из ${total}`"
      >
        <div class="slide__content">
          <h2 class="slide__title">{{ s.title }}</h2>
          <p class="slide__desc">{{ s.description }}</p>
          <div class="slide__content__price_link">
            <a href="#price" class="slide__link" @click="isOpen = true"
              >Узнать стоимость</a
            >
            <svg
              viewBox="0 0 24 24"
              width="20"
              height="20"
              stroke="currentColor"
              stroke-width="1.6"
              fill="none"
              stroke-linecap="round"
              stroke-linejoin="round"
            >
              <polyline points="9 18 15 12 9 6" />
            </svg>
          </div>
        </div>
      </section>
    </div>

    <a class="nav nav--prev" @click.prevent="prev" aria-label="Назад">
      <svg
        viewBox="0 0 24 24"
        width="25"
        height="25"
        stroke="currentColor"
        stroke-width="1.6"
        fill="none"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <polyline points="15 18 9 12 15 6" />
      </svg>
    </a>

    <a class="nav nav--next" @click.prevent="next" aria-label="Вперёд">
      <svg
        viewBox="0 0 24 24"
        width="25"
        height="25"
        stroke="currentColor"
        stroke-width="1.6"
        fill="none"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <polyline points="9 18 15 12 9 6" />
      </svg>
    </a>
  </diм>
</template>

<style scoped>
.slider {
  position: relative;
  width: 100%;
  overflow: hidden;
  border-radius: 14px;
}

.slides {
  display: flex;
  transition: transform 0.45s ease;
}

.slide {
  flex: 0 0 100%;
  min-height: 380px;
  background: linear-gradient(135deg, #999 0%, #fff 100%);
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  padding: 40px 20px;
}

.slide__content {
  max-width: 720px;
  color: #ffffff;
  padding: 0 60px;
}

.slide__title {
  margin: 0 0 12px;
  font-size: 32px;
}
.slide__desc {
  margin: 0 0 20px;
  font-size: 18px;
  opacity: 0.9;
}

.slide__link {
  display: inline-block;
  border: none;
  text-decoration: none;
  color: #ffffff;
  transition: all 0.3s ease;
}
.slide__link:hover {
  text-decoration: underline;
}

/* стрелки */
.nav {
  position: absolute;
  top: 50%;
  translate: 0 -50%;
  width: 44px;
  height: 44px;
  border-radius: 50%;
  display: grid;
  place-items: center;
  background: rgba(0, 0, 0, 0.6);
  color: #fff;
  text-decoration: none;
  transition: background 0.25s ease;
}
.nav:hover {
  background: rgba(0, 0, 0, 0.3);
}
.nav--prev {
  left: 12px;
}
.nav--next {
  right: 12px;
}
.slide__content__price_link {
  display: flex;
  align-items: center;
  margin-top: 50px;
}
</style>
