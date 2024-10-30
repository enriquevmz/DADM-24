<script setup>
import { ref, computed } from "vue";
//modelo 
const header = ref('App lista de Compras');
//---- items ----
//Item model 
const items = ref([
    {id:'0', label: '10 bolillos', purchased: false, highPriority: true}, 
    {id:'1', label: '1 lata de frijol', purchased: true, highPriority: false}, 
    {id:'2', label: '50 g de queso', purchased: false, highPriority: true},
    {id:'3', label: '10 coca cola ligth', purchased: true, highPriority: false}
]);


//Add item
const saveItem = () => {
    //Metodo para agregar otro item a la lista
    items.value.push({
      id: items.value.length + 1, 
      label: newItem.value,
      highPriority: newItemHighPriority.value
    });
    //reiniciando la entrada de texto
    newItem.value = '';
    newItemHighPriority.value = false;
};


//---- formulario -----
 
const newItem = ref(''); 
const newItemHighPriority = ref(false);
const editing = ref(true);


const doEdit = (edit)=>{
  editing.value = edit;
  // Limpiando la entrada de texto
  // en caso de que se oculte o muestre
  // el formulario
  newItem.value = "";
  newItemHighPriority.value = false;
};
const togglePurchased = (item) => {
  item.purchased = !item.purchased;
};

 
// Propiedad computada
const characterCount = computed(() => {
  return newItem.value.length;
});

// Creando propiedad computada que invierte items de la lista
const reversedItems = computed(() => [...items.value].reverse());

</script>

<template>
<div class="header">
    <h1>
    <i class="material-icons shopping-cart-icon">
    local_mall
 </i>
     {{ header }}
</h1>
<button v-if="editing" class="btn" @click="doEdit(false)">Cancelar</button>
<button v-else class="btn btn-primary"  @click="doEdit(true)">Agregar Articulo</button>
</div>


<!-- Agrupando en un div las entradas -->
<form 
  class="add-item fomr" 
  v-if="editing"
  v-on:submit.prevent="saveItem()">
    
    <!-- entrada de texto -->
    <input type="text" 
    placeholder="Add Item "  
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
    <p class="counter">
    {{characterCount}} / 200
  </p>
  
</form>

<!--Lista Objetos-->
    <ul>
        <li v-for="({label,id, purchased, highPriority}, index) in reversedItems"
         @click="togglePurchased(reversedItems[index])"
         :key="id"
         :class="{strikeout: purchased, priority: highPriority}"
         class="amazing"> 
            {{ priority ? "🔥": "🛒"}} {{ label }}
        </li>
    </ul> 
  

<!--Lista Arreglos  
<ul>
  <li
      v-for="item in reversedItems" 
      @click="togglePurchased(item)"
      v-bind:key="item.id"
      :class="{ strikeout: item.purchased, priority: item.highPriority }"
    >
     {{ label }}
</li>
    </ul>-->
    <p v-if="items.length === 0">🥀 NO HAY ELEMENTOS EN LA LISTA 🥀</p>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>