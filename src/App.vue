<script setup>
import { ref, computed } from 'vue'

var name = "DAMIAN"
const counter = ref(0)
const fav = ref([])

const increment = () => {
  counter.value++
}

const decrement = () => {
  counter.value--
}

const reset = () => {
  counter.value = 0
  fav.value = []
}

const add = () => {
    fav.value.push(counter.value)
}

const bloq =computed(()=>{
 const busq = fav.value.find((num) => num === counter.value)
 if(busq === 0) return true
 return busq?true:false
})

</script>

<template>
 <div class="container text-center mt-3">

   <h1>HoLa {{ name }}</h1> <br>
   
   <h2>{{ counter }}</h2>
   <br>
   <div class="btn-group">

     <button @click="decrement" class="btn btn-danger">Restar</button>
     <button @click="increment" class="btn btn-success">Aumentar</button>
     <button @click="reset" class="btn btn-secondary">Reiniciar</button>
     <button @click="add" :disabled="bloq" class="btn btn-primary">Agregar</button>
    </div>
     <h2>Los Favoritos son:</h2>
   <ul class="list-group mt-4">
     <li class="list-group-item" v-for="e in fav" :key="e">
      {{ e }} 
    </li>
  </ul>
</div>
</template>

<style>
h1 {
  color: blue;
}


</style>