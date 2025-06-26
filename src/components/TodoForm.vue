<template>
  <form @submit.prevent="submit" class="form">
    <div class="input-container">
      <span class="input-icon">📝</span>
      <input 
        v-model="title" 
        placeholder="Apa yang ingin kamu kerjakan hari ini?" 
        required 
        class="todo-input"
      />
    </div>
    <button type="submit" class="add-button">
      <span class="button-icon">➕</span>
      <span class="button-text">Tambah</span>
    </button>
  </form>
</template>

<script setup>
import { ref } from 'vue'
import { useTodoStore } from '../store/todo'

const title = ref('')
const todo = useTodoStore()

const submit = async () => {
  if (title.value.trim()) {
    await todo.tambahTodo(title.value)
    title.value = ''
  }
}
</script>

<style scoped>
.form {
  display: flex;
  gap: 12px;
  margin-bottom: 25px;
}

.input-container {
  flex: 1;
  position: relative;
  display: flex;
  align-items: center;
}

.input-icon {
  position: absolute;
  left: 12px;
  font-size: 1.2em;
  color: #7f8c8d;
}

.todo-input {
  flex: 1;
  padding: 12px 15px 12px 40px;
  font-size: 1.05em;
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  transition: all 0.3s ease;
  font-family: 'Inter', sans-serif;
  background: #fff;
}

.todo-input:focus {
  outline: none;
  border-color: #3498db;
  box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.2);
}

.todo-input::placeholder {
  color: #95a5a6;
}

.add-button {
  background-color: #2ecc71;
  color: white;
  border: none;
  padding: 0 20px;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 500;
  display: flex;
  align-items: center;
  gap: 8px;
  transition: all 0.3s ease;
  box-shadow: 0 2px 5px rgba(46, 204, 113, 0.3);
}

.add-button:hover {
  background-color: #27ae60;
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(46, 204, 113, 0.4);
}

.button-icon {
  font-size: 1.2em;
}

.button-text {
  display: none;
}

@media (min-width: 480px) {
  .button-text {
    display: inline;
  }
  
  .add-button {
    padding: 0 20px;
  }
}

@media (max-width: 480px) {
  .form {
    flex-direction: column;
    gap: 10px;
  }
  
  .add-button {
    padding: 10px;
    justify-content: center;
  }
}
</style>
