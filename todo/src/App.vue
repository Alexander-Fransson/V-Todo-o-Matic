<script setup lang="ts">
import { ref } from 'vue'
import TodoItem from './components/todo-item.vue'
import TodoForm from './components/TodoForm.vue'

let todos = ref([])

const remove = (name: string) => {
  todos.value=todos.value.filter(e => e !== name);
}

const add = (name: string) => {
  if(!todos.value.includes(name)){
    todos.value.push(name)
  }
}
</script>

<template>
  <h1>Vu3-T0d0-0-M4t1c</h1>
  <TodoForm @create="add" />
  <TodoItem v-for="todo in todos" :key=todo :name=todo @delete="remove"/>
</template>

<style scoped>
</style>
