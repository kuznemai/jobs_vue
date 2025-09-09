<script setup>
import HeaderMeta from "@/components/HeaderMeta.vue";
import Navbar from "@/components/Navbar.vue";
import Slider from "@/components/Slider.vue";
import slide1 from "../assets/images/preorder1.jpg";
import slide2 from "../assets/images/preorder2.jpg";
import slide1Mobile from "../assets/images/preorder1-mobile.png";
import slide2Mobile from "../assets/images/preorder2-mobile.png";
import {onMounted, onUnmounted, ref} from "vue";

const isMobile = ref(window.innerWidth <= 768)

const slides = ref([]);

function resizeMobile(){
  isMobile.value = window.innerWidth <= 768

  slides.value = [
    {
      id: "1",
      title: "Текст рекламы 1",
      description: "Описание 1",
      image: isMobile.value ? slide1Mobile : slide1,
    },
    {
      id: "2",
      title: "Текст рекламы 2",
      description: "Описание 2",
      image: isMobile.value ? slide2Mobile : slide2 ,
    },
  ]
}

onMounted(() => {
  resizeMobile()
  window.addEventListener("resize", resizeMobile);
} )
onUnmounted(() => {
  window.removeEventListener("resize", resizeMobile);
});
</script>

<template >
  <header id="main" class="header">
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
  max-width: 1200px;
  margin: 20px auto 0;
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
