<script setup>
        
        import PlanPickerItem from './PlanPickerItem.vue';
        import {ref} from 'vue';
//creando una referencia reactiva
const selecPlan = ref(null)

const plans = ref(['El soltero', 'El curioso','El adicto']);
const selectPlan = (name) => {
//ALMACENAR EL PLAN SELECCIONADO 
   selecPlan.value = name;

}
        </script>
<template>
    <div class="plans">
      <PlanPickerItem v-for="plan in plans" 
      :key="plan" 
      :name="plan"
      @select="(name)=> selectPlan(name)"/>
    </div>
    <p>{{ selecPlan }}</p>
</template>

<style scoped>

</style>