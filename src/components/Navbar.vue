<script setup>
import { ref } from "vue";
import ButonSlot from "@/components/ButonSlot.vue";
import BurgerMenu from "@/components/BurgerMenu.vue";

const isOpen = ref(false);
const toggleMenu = () => {
  isOpen.value = !isOpen.value;
};
</script>

<template>
  <div class="menu__wrapper">
    <!-- Бургер (появляется только на мобилках) -->
    <BurgerMenu class="burger" :isOpen="isOpen" @toggle="toggleMenu" />

    <!-- Навигация -->
    <nav class="menu" :class="{ open: isOpen }">
      <ul class="menu__list">
        <li class="menu__item"><a href="#" class="menu__link">Главная</a></li>
        <li class="menu__item"><a href="#" class="menu__link">О нас</a></li>
        <li class="menu__item"><a href="#" class="menu__link">Услуги</a></li>
        <li class="menu__item"><a href="#" class="menu__link">Обратная связь</a></li>
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

/* ===== Десктоп ===== */
.burger {
  display: none; /* скрыт на больших экранах */
}

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
  color: #313131;
  transition: color 0.3s;
  font-weight: 500;
}

.menu__link:hover {
  color: #000;
}

/* ===== Мобильная версия ===== */
@media (max-width: 768px) {
  .burger {
    display: block; /* показываем бургер */
  }

  .menu__wrapper {
    display: block;
    width: 100%;
  }

  .menu {
    position: fixed;
    top: 15%; /* ниже шапки */
    left: -100%;
    height: calc(100vh - 70px);
    width: 100%;
    flex-direction: column;
    align-items: flex-start; /* пункты по левому краю */
    background: #fff;
    padding: 20px;
    transition: left 0.3s ease;
    z-index: 1000;
  }

  .menu.open {
    left: 0;
  }

  .menu__list {
    flex-direction: column;
    gap: 25px;
    font-size: 1.4rem;
    font-weight: 700;
    width: 100%;
  }

  .menu__link {
    width: 100%;
    display: block;
    font-weight: 500;
  }

  .price_button {
    display: none;
  }
}
</style>
