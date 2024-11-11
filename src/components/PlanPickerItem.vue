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
  //impoetando ref funtion
  import {ref} from 'vue';
  //Usando un macro para
  //deginir las props
  //defineProps(['name','planIcon']);
  const props = defineProps({
    name: {
      type: String,
      required: true
    }
  });

  //definiedo event
   const emit = defineEmits(['select'])
  //variable que permite recordar si el plan ha sido seleccionado 
  const selected = ref(false);
  //funcion que permite cambiar el estado de la variable selected
  const selecPlan = () => {
    selected.value = ! selected.value;
  };
  //emitir evento de que ha sido selccionado 
  emit('select', props.name);

 </script>
  
  <style scoped>
  
  </style>