<template>
  <div class="container">
    <todo-app/>
  </div>
</template>

<script>
//importaciones de componente principal
import TodoApp from './components/TodoApp.vue'

export default {
  components: { TodoApp },
  name: 'App'
}
</script>

<style>

body{ 
  height: 100%; 
  background: linear-gradient(90deg, #1d2022 50%, #ffc107 50%); 
  margin-top: 5%;
 }
</style>
