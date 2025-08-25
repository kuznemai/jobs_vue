<script setup>
import Social from "@/components/Social.vue";
</script>

<template>
  <div class="header__meta_wrapper">
    <div class="header__meta_wrapper__left">
      <div class="header__logo">
        <svg
          width="113"
          height="34"
          viewBox="0 0 113 34"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M18.759 0.000107885L4.99893 29.1655L9.43107 31.2288L23.1912 2.06336L18.759 0.000107885Z"
            fill="#121317"
          />
          <path
            d="M25.259 14.166H20.1469V30.1973H25.259V14.166Z"
            fill="#121317"
          />
          <path
            d="M25.2966 28.8472H0V33.9251H25.2966V28.8472Z"
            fill="#121317"
          />
          <path
            d="M40.1198 14.3384H35.5903V33.8845H40.1198V14.3384Z"
            fill="#121317"
          />
          <path
            d="M59.3974 33.9999C53.8593 33.9999 49.3558 29.5236 49.3558 24.0254C49.3558 18.5271 53.8622 14.0508 59.3974 14.0508C64.9326 14.0508 69.439 18.5271 69.439 24.0254C69.439 29.5236 64.9326 33.9999 59.3974 33.9999ZM59.3974 18.6192C56.398 18.6192 53.9579 21.0431 53.9579 24.0225C53.9579 27.0019 56.398 29.4257 59.3974 29.4257C62.3968 29.4257 64.8369 27.0019 64.8369 24.0225C64.8369 21.0431 62.3968 18.6192 59.3974 18.6192Z"
            fill="#121317"
          />
          <path
            d="M80.8599 33.9999C75.3218 33.9999 70.8184 29.5236 70.8184 24.0254C70.8184 18.5271 75.3247 14.0508 80.8599 14.0508C86.3951 14.0508 90.9015 18.5271 90.9015 24.0254C90.9015 29.5236 86.3951 33.9999 80.8599 33.9999ZM80.8599 18.6192C77.8605 18.6192 75.4204 21.0431 75.4204 24.0225C75.4204 27.0019 77.8605 29.4257 80.8599 29.4257C83.8594 29.4257 86.2995 27.0019 86.2995 24.0225C86.2995 21.0431 83.8594 18.6192 80.8599 18.6192Z"
            fill="#121317"
          />
          <path
            d="M85.517 21.2015L68.2913 0.0922852H112.523V4.6636H77.9446L89.0932 18.3229L85.517 21.2015Z"
            fill="#121317"
          />
          <path
            d="M102.323 33.9999C96.7845 33.9999 92.281 29.5236 92.281 24.0254C92.281 18.5271 96.7874 14.0508 102.323 14.0508V18.6221C99.3231 18.6221 96.883 21.0459 96.883 24.0254C96.883 27.0048 99.3231 29.4286 102.323 29.4286C105.322 29.4286 107.762 27.0048 107.762 24.0254H112.364C112.364 29.5265 107.858 33.9999 102.323 33.9999Z"
            fill="#121317"
          />
          <path
            d="M33.9384 14.3384H29.4089V33.8845H33.9384V14.3384Z"
            fill="#121317"
          />
          <path
            d="M46.0956 14.3384H41.566V33.8845H46.0956V14.3384Z"
            fill="#121317"
          />
        </svg>
      </div>

      <div class="header__meta">
        <div class="header__meta__location_image">
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
        </div>
        <span class="header__info">пл.Свободы 7</span>
        <span class="header__info">+7 (831) 423-13-23</span>
      </div>
    </div>
    <div class="header__meta_wrapper__right">
      <span class="header__info">Режим работы:пн-пт 11:00–20:00</span>
      <span class="header__info">сб-вс 11:00–18:00</span>
      <Social></Social>
    </div>
  </div>
</template>

<style scoped>
.header__meta_wrapper {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: end;
  width: 100%;
}
.header__meta_wrapper__left,
.header__meta_wrapper__right {
  display: flex;
  flex-direction: row;
  align-items: baseline;
  gap: 15px;
}

.header__meta {
  margin-left: auto;
  display: flex;
  align-items: center;
  gap: 10px;
}
.header__info {
  font-size: 14px;
  opacity: 60%;
}

.button {
  padding: 8px 16px;
  border: 1px solid #111;
  border-radius: 20px;
  text-decoration: none;
  color: #111;
}
.button:hover {
  background: #111;
  color: #fff;
}
</style>
