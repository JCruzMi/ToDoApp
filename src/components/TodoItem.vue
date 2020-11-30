<template>
  <li class="list-group-item d-flex justify-content-between align-items-center">
      <span 
        role="button" 
        @click="completado(todo.id)"
        :class="{'tachar': todo.estado}"
        >
          {{todo.texto}}
      </span>
      <span 
        role="button" 
        @click="eliminar(todo.id)"
        >
          <i class="fas fa-times"></i>
      </span>
  </li>
</template>

<script>
//importacion de inject
import { inject } from 'vue'

export default {
    //uso de prop todo que llega de TodoList
    props: ['todo'],
    //creacion de setup
    setup(){
        //creacion de constante 'todos' que referencia a la lista
        const todos = inject('todos')
        //funcion para eliminar un 'todo' por id
        const eliminar = id => {
            todos.value = todos.value.filter(item => item.id !== id)
        }
        //funcion que cambia el estado de un 'todo' y retorna todos los 'todo'
        const completado = id => {
            todos.value = todos.value.map(item => {
                if(item.id === id){
                    item.estado = !item.estado
                }
                return item
            })
        }
        //return de eliminar y compeltado que se usan en el componente
        return { eliminar, completado }
    }
}
</script>

<style>
.tachar {
    text-decoration : line-through;
}

</style>