<script setup>
import { ref, onMounted } from "vue";
import SoundOn from "../assets/images/sound-on-svgrepo-com.svg";
import SoundOff from "../assets/images/sound-off-svgrepo-com.svg";

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
      <img v-if="isMuted" :src="SoundOff" alt="Sound Off" width="24" height="24" />
      <img v-else :src="SoundOn" alt="Sound On" width="24" height="24" />
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
  padding: 6px 6px;
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
