<script setup>
import ButonSlot from "@/components/ButonSlot.vue";
import ServicesSliderElement from "@/components/ServicesSliderElement.vue";
import img1 from "@/assets/images/img1.png";
import img2 from "@/assets/images/img2.png";
import img3 from "@/assets/images/img3.png";
import review1 from "@/assets/images/review1.png";
import review2 from "@/assets/images/review2.png";
import review3 from "@/assets/images/review3.png";
import OnePicBlock from "@/components/OnePicBlock.vue";

/* Swiper */
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import { Autoplay } from "swiper/modules";

</script>

<template>
  <section class="services">
    <div class="services__options">
      <h2 class="services__title">Услуги</h2>

      <!-- Swiper slider -->
      <Swiper
          :modules="[Autoplay]"
          :space-between="20"
          :slides-per-view="1.2"
          :breakpoints="{ 768: { slidesPerView: 3, spaceBetween: 30 } }"
          :autoplay="{ delay: 3000, disableOnInteraction: false }"
          class="services__slider"
      >
        <SwiperSlide>
          <ServicesSliderElement :src="img1">
            <template #description>
              <p class="slider_element_description">Модульный ремонт техники Apple</p>
            </template>
          </ServicesSliderElement>
        </SwiperSlide>

        <SwiperSlide>
          <ServicesSliderElement :src="img2">
            <template #description>
              <p class="slider_element_description">Компонентный ремонт техники Apple</p>
            </template>
          </ServicesSliderElement>
        </SwiperSlide>

        <SwiperSlide>
          <ServicesSliderElement :src="img3">
            <template #description>
              <p class="slider_element_description">Замена стекла дисплейного модуля</p>
            </template>
          </ServicesSliderElement>
        </SwiperSlide>
      </Swiper>

      <ButonSlot>Узнать стоимость</ButonSlot>
    </div>

    <OnePicBlock />

    <!-- Reviews -->
    <div class="reviews">
      <div class="reviews__container">
        <Swiper
            :modules="[Autoplay]"
            :space-between="10"
            :slides-per-view="1.2"
            :breakpoints="{ 768: { slidesPerView: 3, spaceBetween: 20 } }"
            :autoplay="{ delay: 3000, disableOnInteraction: false }"
            class="reviews__slider"
        >
          <SwiperSlide>
            <ServicesSliderElement :src="review1" />
          </SwiperSlide>
          <SwiperSlide>
            <ServicesSliderElement :src="review2" />
          </SwiperSlide>
          <SwiperSlide>
            <ServicesSliderElement :src="review3" />
          </SwiperSlide>
          <SwiperSlide>
            <ServicesSliderElement :src="review1" />
          </SwiperSlide>
          <SwiperSlide>
            <ServicesSliderElement :src="review1" />
          </SwiperSlide>
        </Swiper>
        <ButonSlot class="services_review__btn">Узнать больше</ButonSlot>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services {
  display: flex;
  flex-direction: column;
  align-items: flex-start;   /* вместо flex-start */
  gap: 4rem;              /* уменьшил, было 6rem */
  width: 100%;
}

.services__options {
  display: flex;
  flex-direction: column;
  background-color: #f5f5f5;
  padding: 3rem;      /* было 50px, сделаем адаптивнее */
  gap: 2rem;
  box-sizing: border-box;
  width: 100%;
  max-width: 1200px;       /* ограничим ширину внутри */
  margin: 0 auto;          /* центрируем */
}

.services__slider {
  width: 100%;
  max-width: 100%;         /* не выходит за экран */
  height: auto;            /* чтобы Swiper не задавал фиксированную высоту */
}

.services__slider .swiper-slide {
  height: auto;
  display: flex;
  justify-content: center;
}

.services__slider .swiper-slide > * {
  flex: 1;
  max-width: 350px;   /* задаём максимальную ширину карточки */
  min-height: 250px;  /* увеличиваем высоту */

}

.reviews__container {
  width: 100%;
  max-width: 1200px;
  background: #f5f5f5;
}
.reviews__slider {
  width: 100%;
  height: auto;
  overflow: hidden;
}
.reviews__slider .swiper-wrapper {
  width: 100% !important;
}
.reviews__slider .swiper-slide {
  display: flex;
  justify-content: center;
  align-items: center;
  height: auto; /* пусть берёт высоту от содержимого */
}

.reviews__slider .swiper-slide > * {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;


  max-width: 300px;   /* фиксируем ширину карточки */
  min-height: 220px;  /* 🚀 минимальная высота, чтобы карточка не схлопывалась */
  box-sizing: border-box;
  flex: none; /* убрали растягивание */
}


.services__title {
  font-size: 2rem;
  color: #000;
  margin: 0;
}
.slider_element_description {
  color: #000000;
  font-size: 1.2rem;
}


/* --- Мобильная версия --- */
@media (max-width: 768px) {
  .services {
    gap: 3rem;
  }

  .services__options {
    max-width: 100%;
    padding: 2rem 1rem;
    gap: 2rem;
  }

  .services__title {
    font-size: 1.8rem;
  }

  .reviews {
    padding: 2rem 1rem;
  }

  /* Фон на всю ширину */
  .reviews {
    width: 100vw; /* растягиваем на весь экран */
    padding: 3rem 0;
    overflow: hidden;
  }

  /* Контейнер внутри, чтобы центрировать слайды */
  .reviews__container {
    max-width: 1200px;
    margin: 0 auto; /* центрируем слайды */
    padding: 3rem 0;
    box-sizing: border-box;
  }

  /* Swiper */
  .reviews__slider {
    width: 100%;
  }

  /* Слайды */
  .reviews__slider .swiper-slide {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .reviews__slider .swiper-slide > * {
    max-width: 300px;
    min-height: 220px;
    flex: none;
  }

  /* Уменьшаем расстояние между слайдами */
  .reviews__slider.swiper-container {
    --swiper-space-between: 10px; /* кастомная переменная для gap */
  }
  .services_review__btn {
    margin: 1rem;
  }
}
</style>
