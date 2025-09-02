<script setup lang="ts">
import { ref } from "vue";
import logo from "@/assets/images/logo.svg";

const props = defineProps({
  isOpen: Boolean
})
const emit = defineEmits(["toggle"])
</script>

<template>
  <div class="container">
  <div class="details__container">
  <div class="header__logo">
    <img :src="logo" alt="logo" />
  </div>
  <div class="burger-menu">
    <button class="burger-menu__button" @click="emit('toggle')" aria-label="Toggle menu">
      <span :class="{ 'open': isOpen }"></span>
      <span :class="{ 'open': isOpen }"></span>
    </button>
  </div>
  </div>
    <nav v-if="isOpen" class="burger-menu__nav">
      <ul>
        <li><a href="#home">Главная</a></li>
        <li><a href="#about">О нас</a></li>
        <li><a href="#services">Услуги</a></li>
        <li><a href="#feedback">Обратная связь</a></li>
        <li><a href="#reviews">Отзывы</a></li>
        <li><a href="#contacts">Контакты</a></li>
      </ul>
    </nav>
  </div>
</template>

<style scoped>
.details__container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-end;
  width: 100%;
}
.container {
  display: flex;
  flex-direction: column;
}
.burger_logo {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.burger-menu__button {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 30px;
  height: 20px;
  border: none;
  background: none;
  cursor: pointer;
  padding: 0;
  position: relative;
}

.burger-menu__button span {
  position: absolute;
  width: 100%;
  height: 3px;
  background: #000;
  border-radius: 2px;
  transition: transform 0.3s ease, opacity 0.3s ease;
}

/* Верхняя полоска */
.burger-menu__button span:nth-child(1) {
  top: 5px;
}

/* Нижняя полоска */
.burger-menu__button span:nth-child(2) {
  bottom: 5px;
}

/* Анимация в крестик */
.burger-menu__button span.open:nth-child(1) {
  transform: rotate(45deg);
  top: 50%;
}

.burger-menu__button span.open:nth-child(2) {
  transform: rotate(-45deg);
  bottom: 35%;
}

/* Меню */
.burger-menu__nav {
  position: absolute;
  top: 100%;
  left: 0;
  width: 100%;
  background: #fff;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  z-index: 20;
}

.burger-menu__nav ul {
  list-style: none;
  margin: 0;
  padding: 10px 20px;
}

.burger-menu__nav li {
  margin-bottom: 10px;
}

.burger-menu__nav a {
  color: #000;
  text-decoration: none;
  font-weight: 500;
}
.header__info {
  font-size: 14px;
}
</style>
