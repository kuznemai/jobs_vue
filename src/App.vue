<script setup>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import Content from "@/components/Content.vue";
</script>

<template>
  <div class="container">
    <Header></Header>
    <Content></Content>
    <Footer></Footer>
  </div>
</template>

<style>
body {
  background-color: #fff;
  margin: 0;
  font-family:
    "SF Pro Display",
    -apple-system,
    BlinkMacSystemFont,
    "Segoe UI",
    Roboto,
    Helvetica,
    Arial,
    sans-serif;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  max-width: 1200px;
  margin: 0 auto;
  padding-top: 15px;
}
@media (min-width: 1270px) {
  .container {
    max-width: 1270px; /* ограничиваем */
    padding-inline: 40px; /* паддинги вокруг */
  }
}
</style>
