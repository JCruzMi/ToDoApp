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
//imports
import { inject, ref, provide, computed } from 'vue'
//imports componentes
import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'
import TodoFiltro from './TodoFiltro.vue'

export default {
  components: { TodoItem, TodoFooter, TodoFiltro },
  //creacion de setup
  setup(){
      //creacion constantes
      const todosTodos = inject('todos')
      //constante estado que referencia a 'Todos' del filtro
      const estado = ref('Todos')
      //funcion computed que retorna una lista filtrada por el estado de 'estado'
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
      //proporciona el estado
      provide('estado', estado)
      //retorna todos que se usa en el componente
      return {todos}
  }
}
</script>

<style>

</style>