<script setup></script>

<template>
  <div class="social">
    <div class="social">
      <a
        href="https://t.me/jobsnnchat"
        target="_blank"
        rel="noopener"
        class="social__link social__link--tg"
      >
        <img src="../assets/images/telegram.svg" alt="Telegram" />
      </a>
      <a
        href="https://www.instagram.com/jobsnnru"
        target="_blank"
        rel="noopener"
        class="social__link social__link--ig"
        ><img src="../assets/images/instagram.svg" alt="Instagram" />
      </a>
      <a href="https://vk.com/jobsstorenn" class="social__link social__link--vk"
        ><img src="../assets/images/vkontakte.svg" alt="Vkontakte" />
      </a>
    </div>
  </div>
</template>

<style scoped>
.social {
  display: flex;
  align-items: baseline;
  gap: 5px;
}
.social__link {
  padding: 5px 8px;
  border-radius: 5px;
  text-decoration: none;
  font-size: 12px;
}
</style>
