<script setup>
import {ref} from "vue";
//modelo 
const header = ref('App lista de compras');
const items = ref([
    {id:'0', label: '10 bolillos'},
    {id:'1', label:'1 lata de frijoles'},
    {id:'2', label:'Six de chelas'},
    {id:'3', label:'1 Nuetella'},

]);
const newItem =ref('');
const newItemPriority= ref('low');
</script>

<template>
 <h1> 
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }} 
 </h1>
 <input v-model="newItem"
type="text" 
placeholder="Agregar articulo">
<!--Radio Buttons-->
<label>
    <input type="radio" value="low" v-model="newItemPriority">
    Bajo
</label>
<label>
    <input type="radio" value="high" v-model="newItemPriority">
    Alto
</label>
{{ newItemPriority =='low'?'🦊':'🐻'}}
 <ul>
    <li v-for="item in items" :key="item.id"> 🛒 {{  item.label }}</li>
 </ul>
</template>

<style scoped>
.shopping-cart-icon {
    font-size: 3rem;
}
</style>
