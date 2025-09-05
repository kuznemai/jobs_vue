<script setup>
import Social from "@/components/Social.vue";
import logo from "@/assets/images/logo.svg";

const props = defineProps({
  onlyLogo: Boolean,
  onlyContacts: Boolean,
});
</script>

<template>
  <div class="header__meta_wrapper">
    <!-- Только логотип -->
    <template v-if="onlyLogo">
      <div class="header__logo">
        <img :src="logo" alt="logo" />
      </div>
    </template>

    <!-- Только контакты -->
    <template v-else-if="onlyContacts">
      <div class="header__meta">
        <svg
          width="13"
          height="12"
          viewBox="0 0 13 12"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            fill-rule="evenodd"
            clip-rule="evenodd"
            d="M7.70644 4.84042V7.773L9.80534 2.573L4.86704 4.84042H7.70644ZM7.10907 5.44042H2.12344L10.9234 1.3999L7.10907 10.85V5.44042Z"
            fill="#3C3C43"
            fill-opacity="0.6"
          />
        </svg>
        <span class="header__info">пл.Свободы 7</span>
        <span class="header__info">+7 (831) 423-13-23</span>
      </div>
    </template>

    <!-- Полный вариант -->
    <template v-else>
      <div class="header__meta_wrapper__left">
        <div class="header__logo">
          <img :src="logo" alt="logo" />
        </div>
        <div class="header__meta">
          <svg
            width="13"
            height="12"
            viewBox="0 0 13 12"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M7.70644 4.84042V7.773L9.80534 2.573L4.86704 4.84042H7.70644ZM7.10907 5.44042H2.12344L10.9234 1.3999L7.10907 10.85V5.44042Z"
              fill="#3C3C43"
              fill-opacity="0.6"
            />
          </svg>
          <span class="header__info">пл.Свободы 7</span>
          <span class="header__info">+7 (831) 423-13-23</span>
        </div>
      </div>

      <div class="header__meta_wrapper__right">
        <span class="header__info">Режим работы: пн-пт 11:00–20:00</span>
        <span class="header__info">сб-вс 11:00–18:00</span>
        <Social />
      </div>
    </template>
  </div>
</template>

<style scoped>
.header__meta_wrapper {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-end;
  width: 100%;
  padding: 15px 15px 0 15px;
}

.header__meta_wrapper__left,
.header__meta_wrapper__right {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 15px;
}

.header__logo img {
  max-height: 40px;
}

.header__meta {
  display: flex;
  align-items: center;
  gap: 10px;
}

.header__info {
  font-size: 14px;
}

/* --- Мобильная версия --- */
@media (max-width: 768px) {
  .header__meta_wrapper {
    flex-direction: row-reverse;
  }
  .header__meta_wrapper__right {
    display: none;
  }
  .header__meta_wrapper__left {
    margin-right: 10px;
  }
  .header__logo {
    display: none;
  }
}
</style>
