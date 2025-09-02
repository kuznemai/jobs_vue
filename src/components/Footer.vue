<script setup lang="ts">
import Social from "@/components/Social.vue";
</script>

<template>
  <footer class="footer">
    <div class="footer__container">
      <div class="footer__info">
        <h3 class="footer__title">Контакты</h3>
        <a href="tel:+7(831)4231323" class="footer__text footer__text__link"
          >+7 (831) 423 13 23</a
        >

        <h3 class="footer__title">Адрес</h3>
        <p class="footer__text">Нижний Новгород, пл. Свободы 7, 1 этаж</p>

        <h3 class="footer__title">Соцсети</h3>
        <Social></Social>
      </div>

      <div class="footer__map">
        <div style="position: relative; overflow: hidden">
          <a
            href="https://yandex.ru/maps/47/nizhny-novgorod/?utm_medium=mapframe&utm_source=maps"
            style="color: #eee; font-size: 12px; position: absolute; top: 0px"
            >Нижний Новгород</a
          ><a
            href="https://yandex.ru/maps/47/nizhny-novgorod/house/ploshchad_svobody_7/YE0YdgZmTEMHQFtsfX9weH5nYQ==/?ll=44.016559%2C56.319245&utm_medium=mapframe&utm_source=maps&z=17"
            style="color: #eee; font-size: 12px; position: absolute; top: 14px"
            >Площадь Свободы, 7 на карте Нижнего Новгорода, ближайшее метро
            Горьковская — Яндекс Карты</a
          ><iframe
            src="https://yandex.ru/map-widget/v1/?ll=44.016559%2C56.319245&mode=whatshere&whatshere%5Bpoint%5D=44.016560%2C56.319245&whatshere%5Bzoom%5D=17&z=17"
            width="560"
            height="400"
            frameborder="1"
            allowfullscreen="true"
            style="position: relative"
          ></iframe>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  padding: 40px 20px;
  width: 100%;
}
.footer__container {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  gap: 50px;
  margin: 0 auto;
}
.footer__info {
  display: flex;
  flex-direction: column;
  gap: 16px;
}
.footer__title {
  font-size: 14px;
  font-weight: 300;
  margin: 0;
}
.footer__text {
  font-size: 16px;
  margin: 0;
  color: #1c1c1c;
  text-decoration: underline;
}
.footer__text__link {
  text-decoration: none;
}
.footer__socials {
  display: flex;
  gap: 12px;
}

.footer__map {
  max-width: 100%;
  overflow: hidden;
}

/* Адаптив */
@media (max-width: 768px) {
  .footer__container {
    flex-direction: column-reverse;
  }
}
</style>
