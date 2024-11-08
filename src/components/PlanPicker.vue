<script setup>
        
        import PlanItem from './PlanItem.vue';
        import {ref} from 'vue';

const plans = ref(['El soltero', 'El curioso','El adicto']);
        </script>
<template>
    <div class="plans">
      <PlanItem v-for="plan in plans" :key="plan" :name="plan"></PlanItem>
    </div>
</template>

<style scoped>

</style>