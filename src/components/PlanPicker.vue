<script setup>
    import PlanPickerItem from './PlanPickerItem.vue';
    import { ref, onMounted, onUnmounted} from 'vue';
   

    //creando una referencia reactiva para almacenar el plan seleccionado
    const selectedPlan = ref(null);


    const plans = ref(['El Cafetero', 'El Chelero', 'El Choro']);

    const selectPlan = (name) =>{
      selectedPlan.value = name;
    };

 const plansWrapper = ref(null);

    // Intentando obtener la refencia al elemnto .plnas
    console.log("Termnima de ejecutar el script setup🎉");

    onMounted(() => {
    console.log("El componente PlanPicker se ha montado");
    console.log(plansWrapper.value);
    });

    //REgistrando el howk ummaund
    onUnmounted(() => {
      console.log("El componente PlanPicker se ha desmontado")
    });

</script>

<template>
    <div ref="plansWrapper" class="plans">
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