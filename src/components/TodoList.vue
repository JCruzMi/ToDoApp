<template>
  <ul class="list-group">
      <todo-item 
      class="bg-dark text-white"
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        />

        <li v-if="todos.length === 0"
        class="list-group-item bg-dark text-white"
        >
            No hay ToDos.....
        </li>

        <todo-footer 
            v-if="todos.length !== 0"
        />

        <todo-filtro/>
    
  </ul>
</template>

<script>
import { inject, ref, provide, computed } from 'vue'

import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'
import TodoFiltro from './TodoFiltro.vue'

export default {
  components: { TodoItem, TodoFooter, TodoFiltro },
  setup(){
      const todosTodos = inject('todos')

      const estado = ref('Todos')

      const todos = computed(() => {
          if(estado.value === 'Todos'){
            return todosTodos.value
          }
          if(estado.value === 'Activas'){
              return todosTodos.value.filter(item => item.estado === false)
          }else{
              return todosTodos.value.filter(item => item.estado === true)
          }

      })
      provide('estado', estado)

      return {todos}
  }
}
</script>

<style>

</style>