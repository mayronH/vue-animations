<script setup lang="ts">
import { ref } from 'vue'

const todos = ref([
  { text: 'make the bed', id: 1 },
  { text: 'play video games', id: 2 },
])
const newTodo = ref('')
const emit = defineEmits(['bad-value'])
const addTodo = () => {
  if (newTodo.value) {
    const id = Math.random()
    todos.value = [{ text: newTodo.value, id }, ...todos.value]
    newTodo.value = ''
  } else {
    emit('bad-value', 'badValue')
  }
}

const deleteTodo = (id: number) => {
  todos.value = todos.value.filter((todo) => todo.id != id)
}
</script>

<template>
  <div class="todos">
    <input
      v-model="newTodo"
      type="text"
      placeholder="Add a new todo..."
      @keypress.enter="addTodo"
    />
    <div v-if="todos.length">
      <!-- tag = the transition-group will be rendered as ul -->
      <!-- appear = use the transition when the page loads -->
      <transition-group tag="ul" name="list" appear>
        <li v-for="todo in todos" :key="todo.id" @click="deleteTodo(todo.id)">
          {{ todo.text }}
        </li>
      </transition-group>
    </div>
    <div v-else>Woohoo, nothing left todo!</div>
  </div>
</template>

<style>
.todos {
  max-width: 520px;
  margin: 20px auto;
  position: relative;
}
input {
  width: 100%;
  padding: 12px;
  border: 1px solid #eee;
  border-radius: 10px;
  box-sizing: border-box;
  margin-bottom: 20px;
}
.todos ul {
  position: relative;
  padding: 0;
}
.todos li {
  list-style-type: none;
  display: block;
  margin-bottom: 10px;
  padding: 10px;
  background: var(--bg-medium);
  box-shadow: 1px 3px 5px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  width: 100%;
  box-sizing: border-box;
}
.todos li:hover {
  cursor: pointer;
}

/* Simplify version without any unnecessary css */
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: scale(0.6);
}
.list-enter-active,
.list-leave-active {
  transition: all 0.4s cubic-bezier(0.075, 0.82, 0.165, 1);
}

/* apply transition to moving elements */
/* is only applicable to transition groups */
.list-move {
  transition: all 0.3s ease;
}

/* to move transition works properly on element there are leaving the DOM, we need to make it above other elements with position absolute */
.list-leave-active {
  position: absolute;
}
</style>
