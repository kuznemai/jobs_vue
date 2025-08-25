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
</script>

<template>
  <section class="services">
    <div class="services__options">
      <h2 class="services__title">Услуги</h2>
      <div class="slider__elements">
        <ServicesSliderElement :src="img1">
          <template #description>
            <p>Модульный ремонт техники Apple</p>
          </template>
        </ServicesSliderElement>
        <ServicesSliderElement :src="img2">
          <template #description>
            <p>Компонентный ремонт техники Apple</p>
          </template>
        </ServicesSliderElement>
        <ServicesSliderElement :src="img3">
          <template #description>
            <p>Замена стекла дисплейного модуля</p>
          </template>
        </ServicesSliderElement>
      </div>
      <ButonSlot>Узнать стоимость</ButonSlot>
    </div>
    <OnePicBlock></OnePicBlock>
    <!-- Reviews -->
    <div class="reviews">
      <div class="reviews__container">
        <div class="review__elements">
          <ServicesSliderElement :src="review1"></ServicesSliderElement>
          <ServicesSliderElement :src="review2"></ServicesSliderElement>
          <ServicesSliderElement :src="review3"></ServicesSliderElement>
        </div>
        <ButonSlot>Узнать больше</ButonSlot>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services__options {
  display: flex;
  flex-direction: column;
  background-color: #f5f5f5;
  padding: 50px;
  gap: 50px;
}
.services {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 6rem;
}

.services__title {
  font-size: 3rem;
  color: #000;
  margin: 0;
}

.slider__elements {
  display: flex;
  flex-direction: row;
  gap: 2rem;
}

.slider__element p {
  color: #000;
  font-size: 1.4rem;
  margin-top: 0.8rem;
}

/* Reviews */
.reviews {
  width: 100%;
  background-color: #f5f5f5;
  padding: 4rem 0;
  overflow: hidden;
}

.reviews__container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.review__elements {
  display: flex;
  flex-direction: row;
  gap: 2rem;
  overflow: hidden;
  padding: 2rem 0;
}
</style>
