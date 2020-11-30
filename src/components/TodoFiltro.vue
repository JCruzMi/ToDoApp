<template>
  <div class="card mt-3 bg-dark text-white mb-3">
      <div class="card-body d-flex justify-content-between align-items-center">
          <span role="button" @click="filtrar('Activas')" class="example">
              Activas
          </span>
          <span role="button" @click="filtrar('Todos')" class="example">
              Todos
          </span>
          <span role="button" @click="filtrar('Completados')" class="example">
              Completados
          </span>
      </div>
  </div>
  
</template>

<script>
//import de inject
import { inject } from 'vue'

export default {
    //creacion de setup
    setup(){
        //constante estado que proviende de todo TodoList
        const estado = inject('estado')
        //funcion filtrar, optiene un valot y lo añade a la constante estado
        const filtrar = valor =>{
            estado.value = valor
        }
        //return de la funcion que se usa en el componente
        return {filtrar}
    }
}
</script>

<style>
.example {
  font-size: auto;
}
.example:hover {
  color: black;
  text-decoration: underline;
}
</style>