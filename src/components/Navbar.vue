<script setup>
import {ref, watch} from "vue";
import ButonSlot from "@/components/ButonSlot.vue";
import BurgerMenu from "@/components/BurgerMenu.vue";
import RepairPricePopup from "@/components/RepairPricePopup.vue";

const isOpenModal = ref(false);
const isOpen = ref(false);
const toggleMenu = () => {
  isOpen.value = !isOpen.value;
};
watch(isOpen, (newVal) => {
  if (newVal) {
    document.body.style.overflow = "hidden"; // запрет прокрутки
  } else {
    document.body.style.overflow = ""; // возвращаем прокрутку
  }
});


const scrollToSection = (id) => {
  const section = document.getElementById(id);
  if (section) {
    section.scrollIntoView({
      behavior: "smooth",
      block: "start"
    });
    isOpen.value = false;
  }
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
        <li class="menu__item" @click="scrollToSection('whyus')"><a href="#" class="menu__link">О нас</a></li>
        <li class="menu__item" @click="scrollToSection('services')"><a href="#" class="menu__link">Услуги</a></li>
        <li class="menu__item" @click="isOpenModal = true"><a href="#" class="menu__link">Обратная связь</a></li>
        <li class="menu__item" @click="scrollToSection('reviews')"><a href="#" class="menu__link">Отзывы</a></li>
        <li class="menu__item" @click="scrollToSection('footer')"><a href="#" class="menu__link">Контакты</a></li>
      </ul>
    </nav>

    <ButonSlot class="price_button" @click="isOpenModal = true">Узнать стоимость</ButonSlot>
    <RepairPricePopup :is-open-modal = "isOpenModal" @close = "isOpenModal = false"></RepairPricePopup>
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
    top: 100px; /* прилипает ровно к нижней границе хедера */
    left: -100%;
    height: calc(100vh - 70px); /* занимает оставшуюся высоту */
    width: 100%;
    flex-direction: column;
    align-items: flex-start;
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
