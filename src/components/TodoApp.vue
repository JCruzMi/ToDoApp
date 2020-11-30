<template>
  <h1 class="mt-3 text-white">ToDos</h1>
  <todo-form/>
  <todo-list/>
</template>

<script>
//importacion de componentes TodoForm y TodoList
//importacion de ref, provide, watch]Effects
import TodoForm from './TodoForm.vue'
import {ref, provide, watchEffect} from 'vue'
import TodoList from './TodoList.vue'

export default {
  components: { TodoForm, TodoList },
  //creacion de setup
  setup(){
    //constante que guardara todo los todo
    const todos = ref([])
    //provide para usarlo en los demas componentes con inject
    provide('todos',todos)
    //watchEffect para actualización
    watchEffect(() => {
      console.log(todos.value)
    })
  }
  
}
</script>

<style>

</style>