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
import { inject } from 'vue'

export default {
    setup(){
        const estado = inject('estado')

        const filtrar = valor =>{
            estado.value = valor
        }
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