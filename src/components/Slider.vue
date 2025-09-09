<script setup lang="ts">
import { ref } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, Navigation } from "swiper/modules";
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";
import ArrowLeft from "../assets/images/arrow-left.svg";
import ArrowRight from "../assets/images/arrow-right.svg";
import RepairPricePopup from "@/components/RepairPricePopup.vue";

const isOpenModal = ref(false)

const props = defineProps({
  slides: Array
})
// const isBeginning = ref(true);
// const isEnd = ref(false);
//
// const onSwiper = (swiper: any) => {
//   isBeginning.value = swiper.isBeginning;
//   isEnd.value = swiper.isEnd;
//
//   swiper.on("slideChange", () => {
//     isBeginning.value = swiper.isBeginning;
//     isEnd.value = swiper.isEnd;
//   });
// };

</script>

<template>
  <div class="slider">
    <Swiper
        :modules="[Autoplay, Navigation]"
        :navigation="{ nextEl: '.slider__nav--next', prevEl: '.slider__nav--prev' }"
        :autoplay="{ delay: 3000, disableOnInteraction: false }"
        :space-between="20"
        :slides-per-view="1"
        :breakpoints="{ 768: { slidesPerView: 1, spaceBetween: 30 } }"
        class="reviews__slider"
        @swiper="onSwiper"
    >
      <SwiperSlide v-for="slide in slides" :key="slide.id">
        <div
            class="slide__content"
            :style="{ backgroundImage: `url(${slide.image})` }"
        >
<!--          <h2 class="slide__title">{{ slide.title }}</h2>-->
<!--          <p class="slide__desc">{{ slide.description }}</p>-->

          <div class="slide__content__price_link">
            <a href="#price" class="slide__link" @click.prevent="isOpenModal = true">
              Узнать стоимость
              <img src="@/assets/images/arrow-right.svg" alt="стрелка" class="slide__link__arrow" />
            </a>
          </div>
        </div>
      </SwiperSlide>
    </Swiper>

<!--    &lt;!&ndash; кастомные кнопки навигации (передаем селекторы Swiper-у выше) &ndash;&gt;-->
<!--    <button class="slider__nav slider__nav&#45;&#45;prev" :class="{ disabled: isBeginning }">-->
<!--      <img :src="ArrowLeft" alt="prev" />-->
<!--    </button>-->
<!--    <button class="slider__nav slider__nav&#45;&#45;next" :class="{ disabled: isEnd }">-->
<!--      <img :src="ArrowRight" alt="next" />-->
<!--    </button>-->
  </div>
  <RepairPricePopup :is-open-modal="isOpenModal" @close="isOpenModal = false"></RepairPricePopup>
</template>

<style scoped>

.slider {
  position: relative;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  overflow: hidden;
}

/* сам Swiper */
.reviews__slider {
  width: 100%;
  height: 100%;
  overflow: hidden;
}

/* слайд: фон картинкой */
.slide__content {
  position: relative;
  width: 100%;
  height: 500px;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  padding: 36px;
  color: #fff;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  box-sizing: border-box;
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
}

.slide__link__arrow {
  width: 16px;
  height: 16px;
  display: block;
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
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0,0,0,0.8);
  cursor: pointer;
  z-index: 30;
  box-shadow: 0 6px 18px rgba(0,0,0,0.25);
  padding: 0;
  transition: background .18s ease, transform .12s ease;
}

/* стрелки слева/справа */
.slider__nav--prev { left: 12px; }
.slider__nav--next { right: 12px; }

/* изображение внутри кнопки */
.slider__nav img {
  display: block;
  width: 20px;
  height: 20px;
  object-fit: contain;
}

.slider__nav:hover {
  background: rgba(0,0,0,0.65);
  transform: translateY(-50%) scale(1.05);
}

.slider__nav::after { display: none !important; }


.slider__nav:hover {
  background: rgba(0,0,0,0.65);
  transform: translateY(-50%) scale(1.03);
}

.slider__nav:focus {
  outline: none;
  box-shadow: 0 0 0 3px rgba(255,255,255,0.08), 0 6px 18px rgba(0,0,0,0.25);
}

.swiper-button-prev, .swiper-button-next {
  display: none !important;
}

@media (max-width: 768px) {
  .slide__content {
    max-width: 100%;
    height: 75vh;
    padding: 20px;
  }
  .slide__title { font-size: 1.25rem; }
  .slide__desc { font-size: 0.95rem; }
  .slider__nav {
    width: 40px;
    height: 40px;
  }
  .slider__nav img {
    width: 16px;
    height: 16px;
  }
  .slider__nav--prev { left: 8px; }
  .slider__nav--next { right: 8px; }
  .slide__link__arrow {
    width: 12px;
    height: 12px;
  }
  .slider__nav.disabled {
    opacity: 0.4;
    pointer-events: none;
  }

}
</style>