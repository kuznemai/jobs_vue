<script setup>
import HeaderMeta from "@/components/HeaderMeta.vue";
import Navbar from "@/components/Navbar.vue";
import Slider from "@/components/Slider.vue";
import slide1 from "../assets/images/slide-1.jpg";

const slides = [
  {
    id: "1",
    title: "Текст рекламы 1",
    description: "Описание 1",
    image: slide1,
  },
  {
    id: "2",
    title: "Текст рекламы 2",
    description: "Описание 2",
    image: slide1,
  },
];
</script>

<template>
  <header class="header">
    <!-- Верхняя панель с адресом и телефоном -->
    <HeaderMeta />

    <!-- Логотип + меню -->
    <div class="header__bottom">
      <Navbar />
    </div>

    <!-- Слайдер -->
    <div class="header__slider">
      <Slider :slides="slides" />
    </div>
  </header>
</template>

<style scoped>
.header {
  width: 100%;
}

/* Нижняя часть хедера: логотип + меню */
.header__bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 0;
}

/* Слайдер */
.header__slider {
  width: 100%;
  max-width: 1200px; /* ограничиваем ширину */
  margin: 20px auto 0; /* центрируем слайдер */
}

/* --- Адаптив --- */
@media (max-width: 768px) {
  .header__bottom {
    flex-direction: row;
    justify-content: space-between;
    padding: 0 10px;
  }
}
</style>
