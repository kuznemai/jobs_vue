<script setup>
const props = defineProps({
  isOpen: Boolean,
});
const emit = defineEmits(["close", "submit"]);
</script>

<template>
  <div v-if="props.isOpen" class="modal-overlay" @click.self="close">
    <div class="modal">
      <button class="close-btn" @click="close">✕</button>

      <h2>Узнать стоимость ремонта</h2>

      <form @submit.prevent="submitForm">
        <label>
          Ваше имя
          <input type="text" v-model.trim="form.name" />
        </label>
        <span v-if="errors.name" class="error">{{ errors.name }}</span>

        <label>
          Номер телефона
          <input
            type="text"
            v-model.trim="form.phone"
            placeholder="8 (___) ___-__-__"
          />
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
  </div>
</template>

<script>
export default {
  name: "ModalForm",
  props: {
    isOpen: { type: Boolean, default: false },
  },
  emits: ["close", "submit"],
  data() {
    return {
      form: {
        name: "",
        phone: "",
        problem: "",
      },
      errors: {},
    };
  },
  methods: {
    validate() {
      this.errors = {};
      if (!this.form.name) {
        this.errors.name = "Введите имя";
      }
      if (!this.form.phone) {
        this.errors.phone = "Введите телефон";
      } else if (!/^8\s?\(\d{3}\)\s?\d{3}-\d{2}-\d{2}$/.test(this.form.phone)) {
        this.errors.phone = "Телефон должен быть в формате: 8 (XXX) XXX-XX-XX";
      }
      return Object.keys(this.errors).length === 0;
    },
    submitForm() {
      if (this.validate()) {
        this.$emit("submit", { ...this.form });
        this.close();
      }
    },
    close() {
      this.$emit("close");
    },
  },
};
</script>

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
}

.modal {
  background: #fff;
  border-radius: 30px;
  padding: 2rem;
  width: 400px;
  max-width: 90%;
  position: relative;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}

h2 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: #000000;
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
  padding: 0.3rem;
  border: 2px solid #000;
  border-radius: 20px;
  background: #fff;
  cursor: pointer;
  font-size: 1rem;
  transition: all 0.2s ease;
  font-weight: 500;
  align-self: center;
}

.submit-btn:hover {
  background: #f5f5f5;
}
</style>
