<template>
    <div class="flex flex-wrap">
        <div class="lg:w-6/12 w-full lg:mb-0 mb-4  flex items-center justify-center">
          <div class="w-full">
            
            <div class="our-main-services-animate-box animate__animated flex flex-col items-center">
              <div class="lg:mb-6 mb-3">
                <h1
                  class="lg:text-4xl text-2xl font-extrabold text-black dark:text-white"
                >
                  {{ how.title }}
                </h1>
              </div>

              <div class="">
                <div class="item" v-for="(item, index) in how.values" :key="index">
                    <div class="item-text">
                      <p>{{ item }}</p>
                    </div>
                    <div class="icon">
                      <svg width="24" height="24" viewBox="0 0 24 24">
                        <path d="M9 6l6 6-6 6"></path>
                      </svg>
                    </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="lg:w-6/12 w-full lg:mb-0 mb-4 flex items-center">
            <div class="w-full">
              <div class="w-full lg:mb-4 mb-2 rounded-3xl" style="background-color: aquamarine; aspect-ratio:1/1;">
                <NuxtImg src="/images/undraw_programming.svg" class="w-full h-full" />
              </div>
              <div class="our-main-services-animate-box animate__animated">
                
                
              </div>
            </div>
          </div>

          
        <div class="w-full lg:mb-0 mb-4 flex lg:pt-20 pt-4">
            <div v-for="(item, index) in how.results" class="w-1/3 flex justify-center flex-col items-center">
                <div class="flex flex-col items-center mb-3">
                    <h3 :class="{'negative': item.value.startsWith('-'), 'positive': item.value.startsWith('+')}">{{ item.value }}%</h3>
                     <p>{{ item.name }}</p>
                </div>
                <img src="/images/inffits_f_Logo.png" alt="logo" class="stat-icon">
            </div>

        </div>
      </div>
  </template>
  
  <script setup lang="ts">
  // emits
  
// interfaces & types & enums
interface Props {
  how: Object;
}

// props
const props = defineProps<Props>();
  // computed properties
  
  // watches
  
  // methods
  
  // hooks
  </script>
  <style scoped lang="css">

  .item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 0;
  }
  
  .item-text {
    flex: 1;
  }
  
  h3 {
    font-size: 2rem;
    margin: 0;
  }
  
  p {
    margin: 5px 0;
    font-size: 1rem;
    color: #666;
  }

  .stat-icon {
    width: 50px;
    height: 50px;
    margin-top: 10px;
  }
  
  </style>
  