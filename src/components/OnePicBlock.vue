<template>
  <div class="repair__phone__img">
    <picture>
      <!-- для мобильных -->
      <source
        srcset="../assets/images/mobilerepairsmartphone.png"
        media="(max-width: 768px)"
      />
      <!-- дефолт для десктопа -->
      <img
        src="../assets/images/repairsmartphone.png"
        alt="Repairing smartphone"
      />
    </picture>
  </div>
</template>

<style scoped>
.repair__phone__img {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 6rem 3rem;
}

.repair__phone__img img {
  max-width: 100%;
  height: auto;
  display: block;
}
/* --- Мобильная версия --- */
@media (max-width: 768px) {
  .repair__phone__img {
    display: block;
    padding: 0 0 3rem 0;
  }
  .repair__phone__img img {
    width: 100%;
  }
}
</style>
