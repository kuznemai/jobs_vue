<script setup>
import { ref } from "vue";
import ButonSlot from "@/components/ButonSlot.vue";

const isOpen = ref(false);
const toggleMenu = () => {
  isOpen.value = !isOpen.value;
};
</script>

<template>
  <div class="menu__wrapper">
    <!-- Кнопка бургер -->
    <button class="burger" @click="toggleMenu" aria-label="Меню">
      <span :class="{ open: isOpen }"></span>
      <span :class="{ open: isOpen }"></span>
      <span :class="{ open: isOpen }"></span>
    </button>

    <!-- Навигация -->
    <nav class="menu" :class="{ open: isOpen }">
      <ul class="menu__list">
        <li class="menu__item"><a href="#" class="menu__link">Главная</a></li>
        <li class="menu__item"><a href="#" class="menu__link">О нас</a></li>
        <li class="menu__item"><a href="#" class="menu__link">Услуги</a></li>
        <li class="menu__item">
          <a href="#" class="menu__link">Обратная связь</a>
        </li>
        <li class="menu__item"><a href="#" class="menu__link">Отзывы</a></li>
        <li class="menu__item"><a href="#" class="menu__link">Контакты</a></li>
      </ul>
    </nav>
    <ButonSlot class="price_button">Узнать стоимость</ButonSlot>
  </div>
</template>

<style scoped>
.menu__wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

/* Бургер */
.burger {
  display: none;
  flex-direction: column;
  justify-content: space-between;
  width: 26px;
  height: 20px;
  background: none;
  border: none;
  cursor: pointer;
  z-index: 1001;
}

.burger span {
  display: block;
  height: 3px;
  width: 100%;
  background: #1c1c1c;
  border-radius: 2px;
  transition: all 0.3s ease;
}

.burger span.open:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}
.burger span.open:nth-child(2) {
  opacity: 0;
}
.burger span.open:nth-child(3) {
  transform: rotate(-45deg) translate(5px, -5px);
}

/* Меню */
.menu {
  display: flex;
  align-items: center;
  gap: 20px;
}

.menu__list {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  gap: 15px;
}

.menu__item {
  padding: 10px;
}

.menu__link {
  text-decoration: none;
  color: #1c1c1c;
  transition: color 0.3s;
}

.menu__link:hover {
  color: #000000;
}

/* --- Мобильная версия --- */
@media (max-width: 768px) {
  .menu__wrapper {
    display: flex;
    flex-direction: row-reverse;
    width: 100%;
  }
  .burger {
    display: flex;
  }

  .menu {
    position: fixed;
    top: 0;
    right: -100%;
    height: 100vh;
    width: 100%;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background: #fff;
    box-shadow: -2px 0 10px rgba(0, 0, 0, 0.2);
    transition: right 0.3s ease;
    z-index: 1000;
  }

  .menu.open {
    right: 0;
  }

  .menu__list {
    flex-direction: column;
    gap: 25px;
  }

  .menu__item {
    padding: 0;
  }
  .price_button {
    display: none;
  }
}
</style>
