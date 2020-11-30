<template>
    <form @submit.prevent="formulario">
        <input
            type="text"
            class="form-control my-3"
            placeholder="Ingrese tarea"
            v-model.trim="texto"
        >
  </form>
</template>

<script>
//importaciones de ref y inject
import {ref, inject} from 'vue'

export default {
    //creacion de setup
    setup(){
        //creacion de constante todos que es injectada o traida de
        const todos = inject('todos')
        //creacion de constante texto que referencia un ''
        const texto = ref('')
        //funcion formulario que agrega un 'todo/tarea' a la lista de 'todos'
        const formulario = () => {
            //valida que no tenga espacios de más o este vacio el 'todo'
            if(texto.value === ''){
                console.log("vacio")
                return
            }
            //crea el 'todo/tarea'
            const todo = {
                texto: texto.value,
                estado: false,
                id: Date.now()
            }
            //empuja el 'todo/tarea' a 'todos'
            todos.value.push(todo)
            //limpia el ingresar tareas
            texto.value = ''           
            
        }
        //return de formulario y texto que se usan en el componente
        return {formulario, texto}
    }
}
</script>

<style>

</style>