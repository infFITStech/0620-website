<template>
    <div class="floating-button">



        <div class="f-button" style=" background-color: white;">
            <button class=" " @click="floatingButtonClick">
                <img src="/images/inffits_f_Logo.png" alt="Icon" />
            </button>

        </div>
       

    </div>

    


  </template>
  

  <style scoped lang="css">
  .floating-button {
    position: absolute;
    bottom: 40px;
    right: 40px;
    background-color: white;
    border: none;
    border-radius: 50%;
    width: 50px;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    cursor: pointer;
  }
  
  .floating-button img {
    width: 24px;
    height: 24px;
  }

  .floating-button:hover {
    scale: 1.1;
  }
  
</style>
  <script setup lang="ts">
  import useIntersectionObserver from "~/composables/useIntersectionObserver";
  // interfaces & types & enums
  
  // props
  
  // emits
  
  // variables
  const { isIntersected, isIntersectionEnteredIntoView } =
    useIntersectionObserver();
  // computed properties
  
  // watches
  
  // methods
  
  // hooks
  
  onMounted(() => {
    // const animateBoxes = document.querySelectorAll(
    //   ".search-domain-animate-box"
    // ) as any;
  
    // isIntersectionEnteredIntoView(animateBoxes[0], ["animate__fadeInDown"]);
    // isIntersectionEnteredIntoView(animateBoxes[1], ["animate__fadeInUp"]);
  });
  </script>
  <style scoped lang="scss"></style>
  