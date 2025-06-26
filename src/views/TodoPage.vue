<template>
  <div class="container">
    <h2>📝 Todo List</h2>
    <TodoForm />

    <ul class="todo-list">
      <li v-for="item in todo.todos" :key="item.id" class="todo-item">
        <input
          type="checkbox"
          :checked="item.completed"
          @change="toggle(item)"
          class="checkbox"
          id="chk-{{item.id}}"
        />
        <label
          :for="'chk-' + item.id"
          :class="{ selesai: item.completed }"
          class="title"
        >
          <template v-if="editId === item.id">
            <input v-model="editTitle" class="edit-input" />
          </template>
          <template v-else>
            {{ item.title }}
          </template>
        </label>

        <div class="buttons">
          <template v-if="editId === item.id">
            <button @click="saveEdit(item)" class="btn btn-save">💾 Save</button>
            <button @click="cancelEdit" class="btn btn-cancel">✖ Cancel</button>
          </template>
          <template v-else>
            <button @click="startEdit(item)" class="btn btn-edit">✏️ Edit</button>
          </template>
          <button @click="hapus(item.id)" class="btn btn-delete">🗑️</button>
        </div>
      </li>
    </ul>

    <p class="summary">📊 Total: {{ todo.total }} | ✅ Selesai: {{ todo.selesai }}</p>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useTodoStore } from '../store/todo'
import TodoForm from '../components/TodoForm.vue'

const todo = useTodoStore()

const editId = ref(null)
const editTitle = ref('')

const startEdit = (item) => {
  editId.value = item.id
  editTitle.value = item.title
}

const cancelEdit = () => {
  editId.value = null
  editTitle.value = ''
}

const saveEdit = (item) => {
  if (editTitle.value.trim() === '') {
    alert('Judul tidak boleh kosong')
    return
  }
  todo.editTodo(item.id, {
    title: editTitle.value,
    completed: item.completed,
  })
  editId.value = null
  editTitle.value = ''
}

const hapus = (id) => todo.hapusTodo(id)

const toggle = (item) => {
  todo.editTodo(item.id, {
    title: item.title,
    completed: !item.completed,
  })
}

onMounted(() => {
  todo.fetchTodos()
})
</script>

<style scoped>
.container {
  max-width: 650px;
  margin: 30px auto;
  background: linear-gradient(135deg, #f5f7fa 0%, #e4e8f0 100%);
  padding: 30px 35px;
  border-radius: 16px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
}

h2 {
  text-align: center;
  color: #2c3e50;
  margin-bottom: 25px;
  font-weight: 700;
  font-size: 2rem;
  letter-spacing: 0.5px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}

.todo-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.todo-item {
  display: flex;
  align-items: center;
  padding: 15px 20px;
  border-radius: 10px;
  margin-bottom: 12px;
  background: white;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  transition: all 0.3s ease;
  gap: 15px;
}

.todo-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
}

.todo-item.completed {
  background: #f8f9fa;
}

.checkbox {
  width: 20px;
  height: 20px;
  cursor: pointer;
  accent-color: #4CAF50;
  transform: scale(1.2);
  transition: all 0.2s ease;
}

.checkbox:hover {
  transform: scale(1.3);
}

.title {
  flex: 1;
  font-size: 1.15em;
  color: #2c3e50;
  user-select: none;
  cursor: pointer;
  font-weight: 500;
  transition: all 0.3s ease;
}

.selesai {
  text-decoration: line-through;
  color: #95a5a6;
}

.edit-input {
  width: 100%;
  font-size: 1.1em;
  padding: 8px 12px;
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  transition: all 0.3s ease;
  font-family: inherit;
}

.edit-input:focus {
  outline: none;
  border-color: #3498db;
  box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.2);
}

.buttons {
  display: flex;
  gap: 8px;
}

.btn {
  border: none;
  padding: 8px 14px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 0.95em;
  transition: all 0.3s ease;
  user-select: none;
  display: flex;
  align-items: center;
  gap: 6px;
  font-weight: 500;
}

.btn-edit {
  background-color: #3498db;
  color: white;
}

.btn-edit:hover {
  background-color: #2980b9;
  transform: translateY(-1px);
}

.btn-save {
  background-color: #2ecc71;
  color: white;
}

.btn-save:hover {
  background-color: #27ae60;
  transform: translateY(-1px);
}

.btn-cancel {
  background-color: #95a5a6;
  color: white;
}

.btn-cancel:hover {
  background-color: #7f8c8d;
  transform: translateY(-1px);
}

.btn-delete {
  background-color: #e74c3c;
  color: white;
}

.btn-delete:hover {
  background-color: #c0392b;
  transform: translateY(-1px);
}

.summary {
  margin-top: 25px;
  font-weight: 600;
  color: #34495e;
  text-align: center;
  font-size: 1.1em;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 15px;
  background: white;
  padding: 12px;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}
</style>
