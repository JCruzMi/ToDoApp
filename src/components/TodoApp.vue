<template>
  <h1 class="mt-3 text-white">ToDos</h1>
  <todo-form/>
  <todo-list/>
</template>

<script>
import TodoForm from './TodoForm.vue'
import {ref, provide, watchEffect} from 'vue'
import TodoList from './TodoList.vue'

export default {
  components: { TodoForm, TodoList },
  setup(){
    const todos = ref([])
    provide('todos',todos)

    watchEffect(() => {
      console.log(todos.value)
    })
  }
  
}
</script>

<style>

</style>