<template>
    <div class="card">
      <img :src="`/images/${experience.image}`" :alt="experience.name" />
      <span class="card__text">{{ experience.name }}</span>
    </div>
  </template>
  
  <script setup>
  import { defineProps } from 'vue'
  
  const props = defineProps({
    experience: {
      type: Object,
      required: true
    }
  })
  </script>
  
  <style scoped>
  .card {
    border: 1px solid #ccc;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  .card__text {
    font-size: 16px;
    margin-top: 10px;
    display: block;
  }
  </style>
  