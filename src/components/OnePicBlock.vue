<script setup>
import { ref, onMounted } from "vue";

const videoRef = ref(null);
const isMuted = ref(true);

const toggleSound = () => {
  if (videoRef.value) {
    isMuted.value = !isMuted.value;
    videoRef.value.muted = isMuted.value;
  }
};

onMounted(() => {
  if (videoRef.value) {
    videoRef.value.muted = true; // по умолчанию без звука
    videoRef.value.play().catch(() => {
      console.log("Автовоспроизведение заблокировано");
    });
  }
});
</script>

<template>
  <div class="hero">
    <video
        ref="videoRef"
        autoplay
        loop
        playsinline
        muted
        class="bg-video"
    >
      <source src="@/assets/video/IMG_7606.MOV" type="video/mp4" />
    </video>

    <!-- Кнопка звука -->
    <button class="sound-btn" @click="toggleSound">
      <!-- Заглушка для выключенного -->
      <svg v-if="isMuted" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 24 24">
        <path d="M16.5 12a4.5 4.5 0 0 1-4.5 4.5v-2a2.5 2.5 0 0 0 0-5v-2a4.5 4.5 0 0 1 4.5 4.5zm3-6.364-1.414 1.414A7.963 7.963 0 0 1 20 12c0 2.21-.896 4.21-2.343 5.657L19.5 19.5A9.969 9.969 0 0 0 22 12c0-2.761-1.119-5.261-2.5-6.364zM3.707 2.293 2.293 3.707 7.586 9H4v6h4l5 5V14.414l5.293 5.293 1.414-1.414z"/>
      </svg>

      <!-- Громкость включена -->
      <svg v-else xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 24 24">
        <path d="M3 10v4h4l5 5V5l-5 5H3z"/>
        <path d="M14.5 12c0-1.77-1.02-3.29-2.5-4.03v8.06c1.48-.74 2.5-2.26 2.5-4.03z"/>
        <path d="M16.5 12c0 2.21-1.21 4.15-3 5.18v-10.36c1.79 1.03 3 2.97 3 5.18z"/>
      </svg>
    </button>

  </div>
</template>

<style scoped>
.hero {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  gap: 1rem;
  position: relative;
}

.bg-video {
  max-width: 90%;
  border-radius: 20px;
  object-fit: cover;
}

.sound-btn {
  position: absolute;
  right: 10%;
  bottom: 1rem;
  background: #f0f0f0;
  border: none;
  border-radius: 12px;
  padding: 8px 12px;
  cursor: pointer;
  color: #333;
  font-size: 0.9rem;
  display: flex;
  align-items: center;
  gap: 6px;
  transition: background 0.2s ease;
}

.sound-btn:hover {
  background: #e0e0e0;
}
@media (max-width: 768px) {
  .bg-video {
    height: 50vh;
    padding: 0;
    border-radius: 0;
  }
  .sound-btn {
    right: 15%;
  }
}
</style>
