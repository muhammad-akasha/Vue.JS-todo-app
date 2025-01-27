<script setup>
import { ref } from 'vue'
import IconEdit from '@/components/icons/IconEdit.vue'
import DeleteIcon from '@/components/icons/DeleteIcon.vue'

const todo = ref([])
const inp = ref('')
const editinp = ref('')
const editMode = ref(false)

const addTodo = () => {
  if (inp.value.trim()) {
    todo.value.push(inp.value.trim())
    inp.value = ''
  }
}

const startEditing = (index, item) => {
  editMode.value = index // Set the current editing index
  editinp.value = item
}

const editTodo = () => {
  if (editinp.value !== null || editMode.value !== null) {
    todo.value[editMode.value] = editinp.value
    editMode.value = false
  }
}

const deleteTodo = (index) => {
  todo.value.splice(index, 1)
}
</script>

<template>
  <main class="todo-container">
    <h1>Welcome To The Vue JS Todo App</h1>
    <div class="input-container">
      <input class="todoinp" v-model="inp" type="text" placeholder="Add a todo" />
      <button @click="addTodo" class="add-btn">Add Todo</button>
    </div>

    <ul>
      <li class="todo-item" v-for="(item, index) in todo" :key="index">
        <div class="todo-content">
          <input
            v-if="editMode === index"
            class="todoinp"
            v-model="editinp"
            type="text"
            placeholder="edit a todo"
          />
          <button v-if="editMode === index" @click="editTodo" class="edit-btn">Edit Todo</button>
          <h2 v-if="editMode !== index">{{ item }}</h2>
          <div class="todo-actions">
            <span v-if="editMode !== index" @click="startEditing(index, item)" class="edit-icon"
              ><IconEdit
            /></span>
            <span v-if="editMode !== index" @click="deleteTodo(index)" class="delete-icon"
              ><DeleteIcon
            /></span>
          </div>
        </div>
      </li>
    </ul>
  </main>
</template>

<style scoped>
.todo-container {
  width: 600px;
  margin: auto;
  margin-top: 50px;
  background: #f9f9f8;
  padding: 40px;
  box-shadow: 2px 2px 20px rgba(0, 0, 0, 0.1);
  border-radius: 15px;
  font-family: Arial, sans-serif;
}

h1 {
  text-align: center;
  color: #333;
  font-size: 24px;
  margin-bottom: 20px;
}

.input-container {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.todoinp {
  padding: 10px;
  flex: 1;
  border: 2px solid #ccc;
  border-radius: 8px;
  font-size: 16px;
}

.add-btn {
  padding: 10px 15px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.add-btn:hover {
  background-color: #45a049;
}
.edit-btn {
  padding: 10px 15px;
  background-color: #12adc2;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s;
  margin-left: 20px;
}

.edit-btn:hover {
  background-color: #45a049;
}

ul {
  padding: 0;
  list-style-type: none;
}

.todo-item {
  font-size: 20px;
  background-color: #fff;
  padding: 15px;
  margin-bottom: 10px;
  border-radius: 10px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  transition:
    background-color 0.3s,
    transform 0.2s;
}

.todo-item:hover {
  background-color: #f1f1f1;
  transform: translateY(-2px);
}

.todo-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.todo-actions {
  display: flex;
  gap: 15px;
}

.edit-btn,
.delete-btn {
  cursor: pointer;
  transition: transform 0.2s;
}

.edit-btn:hover,
.delete-btn:hover {
  transform: scale(1.2);
}

.edit-icon svg,
.delete-icon svg {
  width: 30px;
  height: 30px;
}
</style>
