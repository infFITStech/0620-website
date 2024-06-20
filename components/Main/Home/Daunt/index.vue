<template>
    <div class="w-full challenges">
        <div v-for="(daunt, index) in props.daunts" :key="index" class="challenge">
          <div class="image-placeholder"></div>
          <p>{{daunt}}</p>
        </div>
        
    </div>
  </template>
  
  <script setup lang="ts">
  // emits
  
// interfaces & types & enums
interface Props {
  daunts: string[];
}

// props
const props = defineProps<Props>();
  // computed properties
  
  // watches
  
  // methods
  
  // hooks
  </script>
  <style scoped lang="css">
  .challenges {
    display: flex;
    justify-content: center;
    gap: 60px;
  }
  
  .challenge {
    text-align: center;
  }
  
  .image-placeholder {
    width: 210px;
    height: 140px;
    background-color: #ddd;
    margin-bottom: 10px;
  }
  </style>
  