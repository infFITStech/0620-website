<template>
  <ul class="flex items-center justify-center overflow-x-scroll " style="-ms-overflow-style: none; scrollbar-width: none; ">
    <li v-for="(item, index) in partners" :key="index" class="min-w-[160px]">
      <div class="lg:mx-8 mx-2 ">
        <!-- lg:w-[160px] lg:h-[64px] -->
        <NuxtImg :src="`/images/${item}`" class="w-full h-full" />
      </div>
    </li>
  </ul>
</template>

<script setup lang="ts">
// interfaces & types & enums

// props

// emits

// variables
const partners = [
  "partner-1.png",
  "partner-2.png",
  "partner-2.png",
  "partner-3.png",
  "partner-4.png",
  "partner-5.png",
];

// computed properties

// watches

// methods

// hooks
</script>
<style scoped lang="scss">
.test{
  color: #e0d58c;
}
</style>
