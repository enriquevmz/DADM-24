<script setup>
import { ref } from "vue";
//modelo 
const header = ref('App lista de Compras');
//---- items ----
//Item model 
const items = ref([
    {id:'0', label: '10 bolillos'}, 
    {id:'1', label: '1 lata de frijol'}, 
    {id:'2', label: '50 g de queso'},
    {id:'3', label: '10 coca cola ligth'}
]);
//Add item
const saveItem = () => {
   items.value.push({id: items.value.length + 1, label: newItem.value});
   //Clear the input
   newItem.value = '';
};


const newItem = ref(''); 
const newItemHighPriority = ref(false);


</script>

<template>
<h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
</h1>

<!-- Agrupando en un div las entradas -->
<form 
  class="add-item fomr" 
  v-on:submit.prevent="saveItem()">
    
    <!-- entrada de texto -->
    <input type="text" 
    placeholder="Agregar"  
    v-model.trim="newItem">
    
    <!-- Caja de seleccion de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      Super Importante 
    </label>

    <!-- Boton -->
    <button class="btn btn-primary">
    AGREGAR</button>
  
</form>
    
    <ul>
        <li v-for="({id,label}, i) in items" :key="id"> {{ i+1 }} {{i%2==0?'🛒':'🌟'}} {{label}} </li>
    </ul>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>
