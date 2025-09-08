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
import {Swiper, SwiperSlide} from "swiper/vue";
import "swiper/css";
import {Autoplay} from "swiper/modules";
import RepairPricePopup from "@/components/RepairPricePopup.vue";
import {ref} from "vue";

const isOpenModal = ref(false)
</script>

<template>
  <section class="services" id="services">
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

      <ButonSlot @click="isOpenModal = true">Узнать стоимость</ButonSlot>
      <RepairPricePopup :isOpenModal="isOpenModal" @close="isOpenModal = false"></RepairPricePopup>
    </div>

    <OnePicBlock/>

    <!-- Reviews -->
    <div class="reviews">
      <div class="reviews__container">
        <Swiper
            :modules="[Autoplay]"
            :space-between="2"
            :slides-per-view="1.2"
            :breakpoints="{ 768: { slidesPerView: 3, spaceBetween: 5 } }"
            :autoplay="{ delay: 3000, disableOnInteraction: false }"
            class="reviews__slider"
            id="reviews"
        >
          <SwiperSlide>
            <ServicesSliderElement :src="review1">
              <template #overlay>
                <img src="@/assets/images/reviewv1.png" alt="icon" class="overlay-icon"/>
                <a href="https://yandex.ru/maps/org/dzhobs_service/116920591134/reviews/"
                   target="_blank"
                   class="read-more">
                  Читать целиком
                </a>
              </template>
            </ServicesSliderElement>
          </SwiperSlide>
          <SwiperSlide>
            <ServicesSliderElement :src="review2">
              <template #overlay>
                <img src="@/assets/images/reviewv2.png" alt="icon" class="overlay-icon"/>
                <a href="https://yandex.ru/maps/org/dzhobs_service/116920591134/reviews/"
                   target="_blank"
                   class="read-more">
                  Читать целиком
                </a>
              </template>
            </ServicesSliderElement>
          </SwiperSlide>
          <SwiperSlide>
            <ServicesSliderElement :src="review3">
              <template #overlay>
                  <img src="@/assets/images/reviewv3.png" alt="icon" class="overlay-icon"/>
                  <a href="https://yandex.ru/maps/org/dzhobs_service/116920591134/reviews/"
                     target="_blank"
                     class="read-more">
                    Читать целиком
                  </a>
              </template>
            </ServicesSliderElement>
          </SwiperSlide>
          <SwiperSlide>
            <ServicesSliderElement :src="review1">
              <template #overlay>
                <img src="@/assets/images/reviewv1.png" alt="icon" class="overlay-icon"/>
                <a href="https://yandex.ru/maps/org/dzhobs_service/116920591134/reviews/"
                   target="_blank"
                   class="read-more">
                  Читать целиком
                </a>
              </template>
            </ServicesSliderElement>
          </SwiperSlide>
          <SwiperSlide>
            <ServicesSliderElement :src="review2">
              <template #overlay>
                <img src="@/assets/images/reviewv2.png" alt="icon" class="overlay-icon"/>
                <a href="https://yandex.ru/maps/org/dzhobs_service/116920591134/reviews/"
                   target="_blank"
                   class="read-more">
                  Читать целиком
                </a>
              </template>
            </ServicesSliderElement>
          </SwiperSlide>
        </Swiper>
        <a href="https://yandex.ru/maps/org/dzhobs_service/116920591134/reviews/" class="read_more_reviews_btn">Узнать больше</a>
      </div>
    </div>
  </section>
</template>

<style scoped>

.image-wrapper .overlay-icon {
  position: absolute;
  top: 20%;
  left: 15px;
  z-index: 5;
  width: 90%;
  padding: 10px;
}
.read-more {
  position: relative;
  bottom: 95px;
  right: 85px;
  text-decoration: none;
  color: #355CED;
  font-size: 0.8rem;
}
.read-more:hover {
  text-decoration: underline;
}
.services {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 4rem;
  width: 100%;
}

.services__options {
  display: flex;
  flex-direction: column;
  background-color: #f5f5f5;
  padding: 3rem;
  gap: 2rem;
  box-sizing: border-box;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}

.services__slider {
  width: 100%;
  max-width: 100%;
  display: flex;
  justify-content: center;
}

.services__slider .swiper-slide > * {
  flex: 1;
  max-width: 350px;
  min-height: 250px;

}

.reviews__container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  background: #f5f5f5;
  padding: 2rem 1rem;
  box-sizing: border-box;

}

.reviews__slider {
  width: 100%;
  height: auto;
  overflow: hidden;
}

.reviews__slider .swiper-slide {
  display: flex;
  justify-content: center;
  align-items: center;
  height: auto;
}

.reviews__slider .swiper-slide > * {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;

  width: 100%;
  max-width: 360px;
  min-height: 220px;
  box-sizing: border-box;
  flex: none;
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
.read_more_reviews_btn{
  text-decoration: none;
  padding: 8px 16px;
  border: 2px solid #111;
  border-radius: 20px;
  color: #111;
  transition: all 0.3s ease;
}
.read_more_reviews_btn:hover {
  background: #111;
  color: #fff;
}

/* --- Мобильная версия --- */
@media (max-width: 768px) {
  .services {
    gap: 3rem;
    align-items: stretch;
  }

  .services__options {
    max-width: 100%;
    padding: 2rem 1rem;
    gap: 2rem;
  }

  .services__title {
    font-size: 1.8rem;
  }

  /* Фон на всю ширину */
  .reviews {
    width: 100vw;
    padding: 1.5rem 0;
    overflow: hidden;
  }

  .reviews__container {
    max-width: 1200px;
    margin: 0 auto;

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

  .reviews__slider.swiper-container {
    --swiper-space-between: 10px;
  }

  .read-more {
    bottom: 80px;
    right: 53px;
  }
  .read_more_reviews_btn:hover {
    background: inherit;
    color: #111111;
  }
}
</style>
