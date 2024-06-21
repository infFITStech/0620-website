<template>
  <div style=" ">
    <div class="flex flex-wrap lg:flex-row flex-col-reverse lg:mb-8 mb-4" >
      <!-- <div class="lg:w-4/12 w-full animate__animated"
      >
        <div class="lg:mb-4 mb-2">
          <h3
            class="text-baseYellow-500 lg:text-base font-bold uppercase lg:text-start text-center"
          >
            {{ $tm("components.default.home.information.title") }}
          </h3>
        </div>
        <div
          class="lg:mb-4 mb-2 lg:text-5xl text-2xl font-extrabold text-black dark:text-white uppercase lg:text-start text-center"
        >
          <h1 class="lg:mb-3 mb-1">
            {{ $tm("components.default.home.information.subtitles.first") }}
          </h1>
          <h1 class="lg:mb-3 mb-1">
            {{ $tm("components.default.home.information.subtitles.second") }}
          </h1>
          <h1 class="lg:mb-3 mb-1">
            {{ $tm("components.default.home.information.subtitles.third") }}
          </h1>
        </div>
        <div class="lg:mb-4 mb-2 lg:text-start text-center lg:pe-14">
          <p class="leading-6">
            {{ $tm("components.default.home.information.text") }}
          </p>
        </div>
        <ElementCharmingLink
          :text="$tm('components.default.home.information.link.text')"
          :link="$tm('components.default.home.information.link.link')"
        />
      </div>
      <div class="lg:w-8/12 w-full lg:mb-0 mb-4">
        <div class="w-full lg:h-[506px] h-[190px]">
          <NuxtImg
            src="/images/undraw_pair_programming.svg"
            class="w-full h-full"
          />
        </div>
      </div> -->

      <div class=" w-full lg:mb-0 mb-4">
        
        <div class="w-full sm:h-[506px] h-[190px] " >
          <!-- <NuxtImg
            src="/images/undraw_pair_programming.svg"
            class="w-full h-full"
          /> -->

          <div class="content h-full w-full flex flex-col items-center justify-center" style=" text-align: center; color: #333; position: relative">
            <div >
              <h1>Boost your eCommerce Sales</h1>
              <h2>with the infFITS AI Service</h2>
              <p>精準的購物體驗，提高商品選購率</p>
              <button @click="a" style="border-radius:999999px ; width:45%; font-size:0.8rem;">Book a Demo</button>
            </div>

            
              <!-- <MainHomeIntroductionSearchDomain /> -->
               <MainHomeIntroductionFoot />
            
          </div>


          


        

          
        </div>

        

      </div>

     

      

      
    </div>

    
  </div>
</template>

<style scoped lang="css">


.content h2, .content h1 {
  font-size: 2.4rem;
  font-weight: bold;
  margin-bottom: 1.5rem;
  scale: 1.3;
  color: #626262;
}

.content h1{
  color: #333
}

.content p {
  font-size: 1.5rem;
  margin-bottom: 2rem;
}

.content button {
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
  color: white;
  background-color: black;
  border: none;
  
  cursor: pointer;
}

.content button:hover {
  background-color: #333;
}
</style>

<script setup lang="ts">
import "animate.css";
// interfaces & types & enums

// props

// emits

// variables

// computed properties

// watches

// methods

// hooks


</script>
<style scoped lang="scss"></style>
