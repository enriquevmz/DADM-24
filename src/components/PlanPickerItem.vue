<template>
    <div @click="selecPlan" class="plan">
      <div class="description">
        <span class="title">
       {{ name }}  {{ selected ? '🦖' : '' }}
        </span>
      </div>
    </div>
  </template>
  
  <script setup>
  //importando la funcion  para crear propiedad computada 

  import { computed } from 'vue';
  //Usando un macro para
  //deginir las props
  //defineProps(['name','planIcon']);
  const props = defineProps({
    name: {
      type: String,
      required: true
    },
    selecPlan: String
  });

  //definiedo event
   const emit = defineEmits(['select'])
  //variable que permite recordar si el plan ha sido seleccionado 
  //funcion que permite cambiar el estado de la variable selected
  const selecPlan = () => {
  //emitir evento de que ha sido selccionado 
  emit('select', props.name);
  }
  //creando una propiedad computada 
  //para  saber si el plan seleccionado 
  const isSelected = computed(() =>{
    return props.name === props.selectedPlan;
  });
 </script>
  
  <style scoped>
  
  </style>