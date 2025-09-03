<script setup></script>

<template>
  <section class="why-us" id="whyus">
    <div class="why-us__content">
      <!-- Введение -->
      <div class="why-us__intro">
        <h1 class="why-us__title">Почему выбирают нас?</h1>
        <p class="why-us__text why-us__text--intro">
          Верните своему гаджету жизнь с нашим сервисом. Подарите своему
          устройству вторую жизнь — доверьте его профессионалам
        </p>
      </div>

      <!-- Детали с изображением -->
      <div class="why-us__details">
        <div class="why-us__details-text">
          Мы предлагаем быстрое и качественное восстановление вашей техники с
          использованием оригинальных запчастей. Гарантия на все виды работ и
          бесплатная диагностика — это наш стандарт! Забудьте о долгом ожидании,
          мы осуществляем ремонт на месте.
        </div>
        <div class="why-us__details-image">
          <img
            src="../assets/images/snapedit_1729250834783%202.png"
            alt="Разобранный телефон"
            class="why-us__image"
          />
        </div>
      </div>
    </div>

    <!-- Опыт (вынесен в отдельную секцию для фона) -->
    <div class="why-us__experience-section">
      <div class="why-us__experience">
        <h2 class="why-us__subtitle">Наш опыт –– ваша уверенность</h2>
        <div class="why-us__experience-items">
          <div class="why-us__experience-item">
            <h4 class="why-us__experience-title">11 лет работы</h4>
            <p class="why-us__experience-text">
              Наш опыт позволяет нам эффективно справляться с любыми неполадками
              и обеспечивать надежное восстановление ваших устройств.
            </p>
          </div>
          <div class="why-us__experience-item">
            <h4 class="why-us__experience-title">20 000 устройств</h4>
            <p class="why-us__experience-text">
              Каждое устройство прошло через наши опытные руки, и мы гарантируем
              качество каждой работы. Доверьте нам свое устройство, и мы вернем
              ему вторую жизнь.
            </p>
          </div>
          <div class="why-us__experience-item">
            <h4 class="why-us__experience-title">10 000 клиентов</h4>
            <p class="why-us__experience-text">
              Наш сервис уже помог множеству клиентов вернуть свои устройства к
              жизни. Довольные клиенты — наша главная ценность.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.why-us {
  padding: 2rem;
  color: black;
}

.why-us__content {
  display: flex;
  flex-direction: column;
  gap: 4rem;
}

/* Введение */
.why-us__intro {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 1rem;
}
.why-us__title {
  font-size: 3.2rem;
  font-weight: 500;
  margin: 0;
}
.why-us__text--intro {
  max-width: 600px;
  font-size: 1rem;
}

/* Детали */
.why-us__details {
  display: flex;
  justify-content: space-between;
  gap: 2rem;
}
.why-us__details-text {
  flex: 0 0 40%;
  font-size: 1rem;
  line-height: 1.5;
}
.why-us__details-image {
  flex: 0 0 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.why-us__image {
  max-width: 100%;
  height: auto;
  object-fit: contain;
}

/* Опыт */
.why-us__experience-section {
  width: 100%;
  background-color: #fff; /* по умолчанию белый */
}
.why-us__experience {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  padding: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}
.why-us__subtitle {
  font-size: 3rem;
  font-weight: 500;
}
.why-us__experience-items {
  display: flex;
  gap: 4rem;
}
.why-us__experience-item {
  flex: 1 1 30%;
}
.why-us__experience-title {
  font-size: 1.4rem;
  margin: 0;
}
.why-us__experience-text {
  font-size: 1rem;
  font-weight: 300;
  margin-top: 0.5rem;
}

/* --- Мобильная версия --- */
@media (max-width: 768px) {
  .why-us {
    padding-bottom: 0;
  }
  .why-us__content {
    padding: 1rem;
  }
  .why-us__title,
  .why-us__subtitle {
    font-size: 1.4rem;
    font-weight: 500;
  }

  .why-us__details {
    flex-direction: column-reverse;
    padding: 1rem 0;
  }

  .why-us__experience-section {
    width: 100vw;
    margin-left: -2rem;
    margin-right: -2rem;
    background-color: #f5f5f5; /* мобильный фон */
  }
  .why-us__experience-item {
    margin: 0 auto;
    max-width: 80%;
    background-color: #fff;
    border-radius: 1rem;
    padding: 2rem;
  }
  .why-us__experience {
    padding: 1.5rem;
  }
  .why-us__experience-items {
    flex-direction: column;
    gap: 2rem;
  }
  .why-us__subtitle {
    margin: 0 auto;
  }
}
</style>
