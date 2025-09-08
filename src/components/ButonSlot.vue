<script setup></script>

<template>
  <div>
    <a href="#price" class="button header__button"><slot></slot></a>
  </div>
</template>

<style scoped>
.header__button {
  padding: 8px 16px;
  border: 1px solid #111;
  border-radius: 20px;
  text-decoration: none;
  color: #111;
  transition: all 0.3s ease;
}

.header__button:hover {
  background: #111;
  color: #fff;
}
/* --- Мобильная версия --- */
@media (max-width: 768px) {
  .header__button:hover {
    background-color: inherit;
    color: #111;
  }
}
</style>
