<!--<script setup lang="ts">-->
<!--import { ref, computed, onMounted, onBeforeUnmount } from "vue";-->
<!--import RepairPricePopup from "@/components/RepairPricePopup.vue";-->

<!--type Slide = {-->
<!--  id?: string | number;-->
<!--  title: string;-->
<!--  description: string;-->
<!--};-->

<!--const props = withDefaults(-->
<!--  defineProps<{-->
<!--    slides: Slide[];-->
<!--    autoplay?: boolean;-->
<!--    interval?: number;-->
<!--  }>(),-->
<!--  {-->
<!--    autoplay: false,-->
<!--    interval: 5000,-->
<!--  },-->
<!--);-->

<!--const current = ref(0);-->
<!--const total = computed(() => props.slides.length);-->

<!--function safeIndex(idx: number) {-->
<!--  return (idx + total.value) % total.value;-->
<!--}-->

<!--function next() {-->
<!--  current.value = safeIndex(current.value + 1);-->
<!--}-->

<!--function prev() {-->
<!--  current.value = safeIndex(current.value - 1);-->
<!--}-->

<!--function goTo(i: number) {-->
<!--  current.value = safeIndex(i);-->
<!--}-->

<!--// autoplay-->
<!--let timer: number | null = null;-->

<!--function startAutoplay() {-->
<!--  if (!props.autoplay || total.value <= 1) return;-->
<!--  stopAutoplay();-->
<!--  timer = window.setInterval(next, props.interval);-->
<!--}-->

<!--function stopAutoplay() {-->
<!--  if (timer) {-->
<!--    clearInterval(timer);-->
<!--    timer = null;-->
<!--  }-->
<!--}-->

<!--// клавиатура-->
<!--function onKeydown(e: KeyboardEvent) {-->
<!--  if (e.key === "ArrowRight") next();-->
<!--  else if (e.key === "ArrowLeft") prev();-->
<!--}-->

<!--onMounted(() => {-->
<!--  window.addEventListener("keydown", onKeydown);-->
<!--  startAutoplay();-->
<!--});-->
<!--onBeforeUnmount(() => {-->
<!--  window.removeEventListener("keydown", onKeydown);-->
<!--  stopAutoplay();-->
<!--});-->

<!--const isOpen = ref(false);-->
<!--</script>-->

<!--<template>-->
<!--  <RepairPricePopup :isOpen="isOpen" @close="isOpen = false" />-->

<!--  <div class="slider" @mouseenter="stopAutoplay" @mouseleave="startAutoplay">-->
<!--    <div-->
<!--      class="slides"-->
<!--      :style="{ transform: `translateX(-${current * 100}%)` }"-->
<!--    >-->
<!--      <section-->
<!--        v-for="(s, i) in slides"-->
<!--        :key="s.id ?? i"-->
<!--        class="slide"-->
<!--        role="group"-->
<!--        :aria-label="`${i + 1} из ${total}`"-->
<!--      >-->
<!--        <div class="slide__content">-->
<!--          <h2 class="slide__title">{{ s.title }}</h2>-->
<!--          <p class="slide__desc">{{ s.description }}</p>-->
<!--          <div class="slide__content__price_link">-->
<!--            <a href="#price" class="slide__link" @click="isOpen = true">-->
<!--              Узнать стоимость-->
<!--            </a>-->
<!--            <svg-->
<!--              viewBox="0 0 24 24"-->
<!--              width="20"-->
<!--              height="20"-->
<!--              stroke="currentColor"-->
<!--              stroke-width="1.6"-->
<!--              fill="none"-->
<!--              stroke-linecap="round"-->
<!--              stroke-linejoin="round"-->
<!--            >-->
<!--              <polyline points="9 18 15 12 9 6" />-->
<!--            </svg>-->
<!--          </div>-->
<!--        </div>-->
<!--      </section>-->
<!--    </div>-->

<!--    <a class="nav nav&#45;&#45;prev" @click.prevent="prev" aria-label="Назад">-->
<!--      <svg-->
<!--        viewBox="0 0 24 24"-->
<!--        width="25"-->
<!--        height="25"-->
<!--        stroke="currentColor"-->
<!--        stroke-width="1.6"-->
<!--        fill="none"-->
<!--        stroke-linecap="round"-->
<!--        stroke-linejoin="round"-->
<!--      >-->
<!--        <polyline points="15 18 9 12 15 6" />-->
<!--      </svg>-->
<!--    </a>-->

<!--    <a class="nav nav&#45;&#45;next" @click.prevent="next" aria-label="Вперёд">-->
<!--      <svg-->
<!--        viewBox="0 0 24 24"-->
<!--        width="25"-->
<!--        height="25"-->
<!--        stroke="currentColor"-->
<!--        stroke-width="1.6"-->
<!--        fill="none"-->
<!--        stroke-linecap="round"-->
<!--        stroke-linejoin="round"-->
<!--      >-->
<!--        <polyline points="9 18 15 12 9 6" />-->
<!--      </svg>-->
<!--    </a>-->
<!--  </div>-->
<!--</template>-->

<!--<style scoped>-->
<!--.slider {-->
<!--  position: relative;-->
<!--  width: 100%;-->
<!--  overflow: hidden;-->
<!--  border-radius: 14px;-->
<!--}-->

<!--.slides {-->
<!--  display: flex;-->
<!--  transition: transform 0.45s ease;-->
<!--}-->

<!--.slide {-->
<!--  flex: 0 0 100%;-->
<!--  min-height: 500px;-->
<!--  display: flex;-->
<!--  justify-content: space-between;-->
<!--  align-items: flex-end;-->
<!--  padding: 40px 20px;-->
<!--  background: linear-gradient(135deg, #999 0%, #fff 100%);-->
<!--}-->

<!--.slide__content {-->
<!--  max-width: 720px;-->
<!--  color: #ffffff;-->
<!--  padding: 0 60px;-->
<!--}-->

<!--.slide__title {-->
<!--  margin: 0 0 12px;-->
<!--  font-size: 32px;-->
<!--}-->

<!--.slide__desc {-->
<!--  margin: 0 0 20px;-->
<!--  font-size: 18px;-->
<!--  opacity: 0.9;-->
<!--}-->

<!--.slide__link {-->
<!--  display: inline-block;-->
<!--  border: none;-->
<!--  text-decoration: none;-->
<!--  color: #ffffff;-->
<!--  transition: all 0.3s ease;-->
<!--}-->

<!--.slide__link:hover {-->
<!--  text-decoration: underline;-->
<!--}-->

<!--/* стрелки */-->
<!--.nav {-->
<!--  position: absolute;-->
<!--  top: 50%;-->
<!--  translate: 0 -50%;-->
<!--  width: 44px;-->
<!--  height: 44px;-->
<!--  border-radius: 50%;-->
<!--  display: grid;-->
<!--  place-items: center;-->
<!--  background: rgba(0, 0, 0, 0.6);-->
<!--  color: #fff;-->
<!--  text-decoration: none;-->
<!--  transition: background 0.25s ease;-->
<!--}-->

<!--.nav:hover {-->
<!--  background: rgba(0, 0, 0, 0.3);-->
<!--}-->

<!--.nav&#45;&#45;prev {-->
<!--  left: 12px;-->
<!--}-->

<!--.nav&#45;&#45;next {-->
<!--  right: 12px;-->
<!--}-->

<!--.slide__content__price_link {-->
<!--  display: flex;-->
<!--  align-items: center;-->
<!--  margin-top: 50px;-->
<!--}-->

<!--/* -&#45;&#45; Мобильная версия -&#45;&#45; */-->
<!--@media (max-width: 768px) {-->
<!--  .slider {-->
<!--    border-radius: 0;-->
<!--  }-->
<!--  .slide__content {-->
<!--    padding: 0 20px;-->
<!--  }-->
<!--  .slide__title {-->
<!--    font-size: 24px;-->
<!--  }-->
<!--  .slide__desc {-->
<!--    font-size: 16px;-->
<!--  }-->
<!--}-->
<!--</style>-->
<script setup lang="ts">
import { ref } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, Navigation, Pagination } from "swiper/modules"; // ✅ вот так
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";

const isOpen = ref(false)

const props = defineProps({
  slides: Array
})
</script>

<template>
  <div class="slider">
    <Swiper
        :modules="[Autoplay, Navigation]"
        :navigation="{ nextEl: '.slider__nav--next', prevEl: '.slider__nav--prev' }"
        :autoplay="{ delay: 3000, disableOnInteraction: false }"
        :space-between="20"
        :slides-per-view="1"
        :breakpoints="{ 768: { slidesPerView: 3, spaceBetween: 30 } }"
        class="reviews__slider"
    >
      <SwiperSlide v-for="slide in slides" :key="slide.id">
        <div
            class="slide__content"
            :style="{ backgroundImage: `url(${slide.image})` }"
        >
          <h2 class="slide__title">{{ slide.title }}</h2>
          <p class="slide__desc">{{ slide.description }}</p>

          <div class="slide__content__price_link">
            <a href="#price" class="slide__link" @click.prevent="isOpen = true">Узнать стоимость</a>
          </div>
        </div>
      </SwiperSlide>
    </Swiper>

    <!-- кастомные кнопки навигации (передаем селекторы Swiper-у выше) -->
    <button class="slider__nav slider__nav--prev" aria-label="Previous slide"></button>
    <button class="slider__nav slider__nav--next" aria-label="Next slide"></button>
  </div>
</template>

<style scoped>
/* контейнер слайдера */
.slider {
  position: relative;
  width: 100%;
  overflow: visible;
  border-radius: 14px;
}

/* сам Swiper */
.reviews__slider {
  width: 100%;
}

/* слайд: фон картинкой, текст внизу */
.slide__content {
  position: relative;
  width: 100%;
  height: 500px; /* можно подкорректировать */
  border-radius: 12px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  justify-content: flex-end; /* текст внизу */
  padding: 36px;
  color: #fff;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

/* заголовок/описание */
.slide__title {
  margin: 0 0 8px;
  font-size: 1.6rem;
  font-weight: 600;
  text-shadow: 0 2px 8px rgba(0,0,0,0.45);
}
.slide__desc {
  margin: 0 0 10px;
  font-size: 1rem;
  opacity: 0.95;
  text-shadow: 0 2px 8px rgba(0,0,0,0.35);
}

/* "кнопка" — белый текст со стрелкой (без фона) */
.slide__content__price_link {
  margin-top: 8px;
}
.slide__link {
  color: #ffffff;
  text-decoration: none;
  font-weight: 600;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  /* стрелка добавляется через псевдоэлемент */
}
.slide__link::after {
  content: "→";
  display: inline-block;
  font-weight: 700;
  transform: translateY(-1px);
}

/* === КАСТОМНЫЕ КНОПКИ НАВИГАЦИИ === */
.slider__nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 44px;
  height: 44px;
  border-radius: 50%;
  border: none;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background: rgba(0,0,0,0.8); /* тёмный фон */
  color: #fff;
  cursor: pointer;
  z-index: 30;
  box-shadow: 0 6px 18px rgba(0,0,0,0.25);
  transition: background .18s ease, transform .12s ease;
  padding: 0;
}

/* 위치 слева/справа */
.slider__nav--prev { left: 12px; }
.slider__nav--next { right: 12px; }

/* убираем стандартные ::after Swiper (на всякий случай) */
.slider__nav::after { display: none !important; }

/* вставляем белые стрелки через ::before (чёткие и контрастные) */
.slider__nav--prev::before,
.slider__nav--next::before {
  content: "";
  font-size: 35px;
  line-height: 0.5;
  color: #fff;
  display: inline-block;
  width: 18px;
  height: 18px;
  text-align: center;
  font-weight: 300;
}

/* разные символы для prev / next */
.slider__nav--prev::before { content: "‹"; } /* левый угол */
.slider__nav--next::before { content: "›"; } /* правый угол */

.slider__nav:hover {
  background: rgba(0,0,0,0.65);
  transform: translateY(-50%) scale(1.03);
}

/* фокус (доступность) */
.slider__nav:focus {
  outline: none;
  box-shadow: 0 0 0 3px rgba(255,255,255,0.08), 0 6px 18px rgba(0,0,0,0.25);
}

/* скроем дефолтные Swiper-кнопки (на случай, если они где-то ещё появились) */
.swiper-button-prev, .swiper-button-next {
  display: none !important;
}

/* адаптив */
@media (max-width: 768px) {
  .slide__content { height: 420px; padding: 20px; }
  .slider__nav { width: 40px; height: 40px; }
  .slider__nav--prev { left: 8px; }
  .slider__nav--next { right: 8px; }
  .slide__title { font-size: 1.25rem; }
  .slide__desc { font-size: 0.95rem; }
}
</style>