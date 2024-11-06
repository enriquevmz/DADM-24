<script setup>
import { ref } from 'vue';
import planItem from './components/plan-item.vue';
const planes = 
ref(['El cafetero', 'El chelas', 'El genio']);
</script>

<template>
  <header>
    <div>
      <div style="text-align: center;"></div>
      <span id="logo">ITGAM BOX EXPIRINANS</span><br>
      <img src="./assets/logo.png" alt="logo">
    </div>
  </header>

  <div class="content">
    <h1 class="title">Coffee Plans</h1>

    <h2 class="subtitle">
      Viajamos por el mundo para encontrar el mejor café de origen único para ti
    </h2>

    <div class="plans">
      <plan-item v-for="plan in planes" :key="plan" :name="plan"/>
      </div>
  </div>
</template>

<style scoped>
</style>