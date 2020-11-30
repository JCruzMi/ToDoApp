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
import { inject,computed } from 'vue'

export default {
    setup(){
        const todos = inject('todos')

        const contar = computed(() => {
            return todos.value.filter(item => item.estado === false ).length
        })

        const eliminar = () => {
            todos.value = todos.value.filter(item => item.estado === false)
        }

        return { contar,eliminar }
    }
}

</script>

<style>

</style>