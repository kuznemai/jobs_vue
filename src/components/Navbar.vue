<script setup>
import ButonSlot from "@/components/ButonSlot.vue";
</script>

<template>
  <div class="menu__wrapper">
    <div>
      <nav class="menu">
        <ul class="menu__list">
          <li class="menu__item"><a href="#" class="menu__link">Главная</a></li>
          <li class="menu__item"><a href="#" class="menu__link">О нас</a></li>
          <li class="menu__item"><a href="#" class="menu__link">Услуги</a></li>
          <li class="menu__item">
            <a href="#" class="menu__link">Обратная связь</a>
          </li>
          <li class="menu__item"><a href="#" class="menu__link">Отзывы</a></li>
          <li class="menu__item">
            <a href="#" class="menu__link">Контакты</a>
          </li>
        </ul>
      </nav>
    </div>
    <ButonSlot>Узнать стоимость</ButonSlot>
  </div>
</template>

<style scoped>
.menu__wrapper {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  width: 100%;
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
</style>
