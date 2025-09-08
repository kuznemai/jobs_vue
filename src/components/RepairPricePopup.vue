<script setup>
import { reactive, ref, watch } from "vue";

const props = defineProps({
  isOpenModal: Boolean,
});
const emit = defineEmits(["close"]);

// Форма
const form = reactive({
  name: "",
  phone: "",
  problem: "",
});

// Ошибки
const errors = reactive({
  name: "",
  phone: "",
});

// Флаги состояния
const isSubmitted = ref(false);
const isLoading = ref(false);

// Нормализация телефона
function normalizePhone(input) {
  let digits = input.replace(/\D/g, "");
  if (!digits.startsWith("8")) digits = "8" + digits;
  return digits.slice(0, 11);
}

// Валидация формы
function validate() {
  errors.name = "";
  errors.phone = "";

  if (!form.name.trim()) errors.name = "Введите имя";

  form.phone = normalizePhone(form.phone);

  if (!form.phone) {
    errors.phone = "Введите телефон";
  } else if (!/^8\d{10}$/.test(form.phone)) {
    errors.phone = "Телефон должен быть в формате: 89000000000";
  }

  return !errors.name && !errors.phone;
}

// Отправка формы на Formspree
async function submitForm() {
  if (!validate()) return;

  isLoading.value = true;

  try {
    const res = await fetch("https://formspree.io/f/xovnynqp", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({
        name: form.name,
        phone: form.phone,
        problem: form.problem,
      }),
    });

    if (res.ok) {
      isSubmitted.value = true;
      form.name = "";
      form.phone = "";
      form.problem = "";
    } else {
      alert("❌ Ошибка при отправке. Попробуйте позже.");
    }
  } catch (err) {
    console.error("Ошибка:", err);
    alert("⚠️ Сеть недоступна или сервер не отвечает.");
  } finally {
    isLoading.value = false;
  }
}

// Закрытие модалки
function  close() {
  emit("close");
  isSubmitted.value = false;
  isLoading.value = false;
}

// Сброс формы, если модалка закрыта извне
watch(() => props.isOpenModal, (val) => {
  if (!val) {
    isSubmitted.value = false;
    isLoading.value = false;
  }
});
</script>

<template>
  <div v-if="props.isOpenModal" class="modal-overlay" @click.self="close">
    <div class="modal">
      <button class="close-btn" @click="close">✕</button>

      <h2>Узнать стоимость ремонта</h2>

      <div v-if="isLoading" class="spinner-wrapper">
        <div class="spinner"></div>
      </div>

      <div v-else-if="!isSubmitted">
        <form @submit.prevent="submitForm">
          <label>
            Ваше имя
            <input type="text" v-model.trim="form.name" />
          </label>
          <span v-if="errors.name" class="error">{{ errors.name }}</span>

          <label>
            Номер телефона
            <input type="text" v-model.trim="form.phone" placeholder="89XXXXXXXXX" />
          </label>
          <span v-if="errors.phone" class="error">{{ errors.phone }}</span>

          <label>
            Описание проблемы
            <textarea v-model.trim="form.problem"></textarea>
          </label>

          <p class="info">
            Оставьте свои данные, менеджер с вами свяжется. <br />
            Или позвоните по телефону <strong>8 (831) 423 13 23</strong>
          </p>

          <button type="submit" class="submit-btn">Отправить</button>
        </form>
      </div>

      <div v-else class="submitted-message">
        ✅ Заявка отправлена!
      </div>
    </div>
  </div>
</template>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  padding: 20px;
}

.modal {
  background: #fff;
  border-radius: 30px;
  padding: 2rem;
  width: 400px;
  max-width: 100%;
  position: relative;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.close-btn {
  position: absolute;
  top: 12px;
  right: 12px;
  border: none;
  background: transparent;
  font-size: 1.2rem;
  cursor: pointer;
}

label {
  display: block;
  margin: 0.5rem 0 0.2rem;
  font-size: 0.9rem;
  color: #333;
}

input,
textarea {
  width: 100%;
  padding: 0.6rem;
  margin-bottom: 0.5rem;
  border-radius: 6px;
  border: 1px solid #ccc;
  font-size: 1rem;
}

textarea {
  min-height: 70px;
  resize: vertical;
}

.error {
  color: red;
  font-size: 0.8rem;
  margin-bottom: 0.5rem;
  display: block;
}

.info {
  font-size: 0.85rem;
  color: #666;
  margin: 1rem 0;
}

.submit-btn {
  width: 100%;
  padding: 0.5rem;
  border: 2px solid #000;
  border-radius: 20px;
  background: #fff;
  cursor: pointer;
  font-size: 1rem;
  transition: all 0.2s ease;
  font-weight: 500;
}

.submit-btn:hover {
  background: #f5f5f5;
}

.submitted-message {
  font-size: 1.2rem;
  color: green;
  text-align: center;
  padding: 2rem 0;
}

/* --- Спиннер --- */
.spinner-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2rem 0;
}

.spinner {
  border: 4px solid #f3f3f3; /* светлый фон */
  border-top: 4px solid #000; /* цвет крутящегося сегмента */
  border-radius: 50%;
  width: 40px;
  height: 40px;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

@media (max-width: 768px) {
  .modal-overlay {
    align-items: flex-start;
    padding-top: 40px;
    overflow-y: auto;
  }

  .modal {
    width: 90%;
    max-width: 90%;
    padding: 1.5rem;
    border-radius: 20px;
    max-height: 90vh;
    overflow-y: auto;
  }
}
</style>
