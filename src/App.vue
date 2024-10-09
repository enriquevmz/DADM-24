<script setup>
import { ref } from "vue";
//modelo 
const header = ref('App lista de Compras');
//---- items ----
//Item model 
const items = ref([
    {id:'0', label: '10 bolillos', purchased: false, priority: true}, 
    {id:'1', label: '1 lata de frijol', purchased: true, priority: false}, 
    {id:'2', label: '50 g de queso', purchased: false, priority: true},
    {id:'3', label: '10 coca cola ligth', purchased: true, priority: false}
]);
//Add item
const saveItem = () => {
   items.value.push({id: items.value.length + 1, label: newItem.value});
   //Clear the input
   newItem.value = '';
};

//---- formulario -----
 
const newItem = ref(''); 
const newItemHighPriority = ref(false);
const editing = ref(true);
const activateEdition = (activate) => {
    editing.value = activate;
};

</script>

<template>
<div class="header">
    <h1>
    <i class="material-icons shopping-cart-icon">
    local_mall
 </i>
     {{ header }}
</h1>
<button v-if="editing" class="btn" @click="activateEdition(false)">Cancelar</button>
<button v-else class="btn btn-primary"  @click="activateEdition(true)">Agregar Articulo</button>
</div>


<!-- Agrupando en un div las entradas -->
<form 
  class="add-item fomr" 
  v-if="editing"
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
    <button 
    :disabled="newItem.length === 0" 
    class="btn btn-primary">
    AGREGAR</button>
  
</form>
    
    <ul>
        <li v-for="({label,id, purchased, priority}, i) in items"
         :key="id"
         :class="{strikeout: purchased, priority: priority}"
         class="amazing"> 
            {{ priority ? "🔥": "🛒"}} {{ label }}
        </li>
    </ul>
    <p v-if="items.length === 0">🥀 NO HAY ELEMENTOS EN LA LISTA 🥀</p>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>
