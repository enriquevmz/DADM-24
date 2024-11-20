<script setup>
    import PlanPickerItem from './PlanPickerItem.vue';
    import { ref, onMounted} from 'vue';

    //creando una referencia reactiva para almacenar el plan seleccionado
    const selectedPlan = ref(null);


    const plans = ref(['El Cafetero', 'El Chelero', 'El Choro']);

    const selectPlan = (name) =>{
      selectedPlan.value = name;
    };

    // Intentando obtener la refencia al elemnto .plnas
    console.log("Termnima de ejecutar el script setup🎉");

</script>

<template>
    <div class="plans">
      <PlanPickerItem  
      v-for = "plan in plans" 
      :key="plan" 
      :name="plan"
      @select="selectPlan"
      :selectPlan="selectedPlan"/>
    </div>
</template>

<style scoped>

</style>