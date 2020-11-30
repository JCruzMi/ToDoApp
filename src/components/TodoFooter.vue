<template>
  <li class="list-group-item d-flex justify-content-between align-items-center bg-dark text-white">
      <span>
          {{contar}} activos
      </span>
      <span 
        role="button" 
        @click="eliminar"
        >
            Eliminar Completados
      </span>
  </li>
</template>

<script>
//importacion de inject y computed
import { inject,computed } from 'vue'

export default {
    //creacaion de setup
    setup(){
        //constante todos que refiere a todos de TodoApp
        const todos = inject('todos')
        //funcion contar para mostrar los todos activos
        const contar = computed(() => {
            return todos.value.filter(item => item.estado === false ).length
        })
        //funcion eliminar que elimina de la constante 'todos' todas las tareas marcadas
        const eliminar = () => {
            todos.value = todos.value.filter(item => item.estado === false)
        }
        //return de contar y eliminar que se usan en el componente
        return { contar,eliminar }
    }
}

</script>

<style>

</style>