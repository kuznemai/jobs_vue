<script setup>
import HeaderMeta from "@/components/HeaderMeta.vue";
import Navbar from "@/components/Navbar.vue";
import Slider from "@/components/Slider.vue";

const ads = [
  {
    title: "Текст рекламы",
    description: "Описание рекламы",
    image: "/images/slide-1.jpg",
  },
  {
    title: "Текст рекламы3",
    description: "Описание рекламы3",
    image: "/images/slide-1.jpg",
  },
];
</script>

<template>
  <HeaderMeta></HeaderMeta>
  <Navbar></Navbar>
  <Slider :slides="ads" autoplay :interval="4000" />
</template>

<style scoped></style>
