<template>
    <div style="background: linear-gradient(135deg, #fdfbfb 0%, #ebedee 100%); " class="flex">
       
  
        <div class="lg:w-6/12 w-full lg:mb-0 mb-4  flex items-center justify-center">
            <div class="w-full  flex items-center justify-center flex-col">
              
                <h1>Experience a conversion rocket for a free trial</h1>
                <p class="w-full">立即預約試用，提升平台轉換率</p>
            </div>
          </div>
          



          <div class="lg:w-6/12 w-full lg:mb-0 mb-4 flex items-center justify-center">
              <div class="">
                <div class="form-container flex flex-col items-center justify-center m-12">
                    <img src="/images/infFITS_Logo.png" alt="logo" class="max-w-60">
                    <form @submit.prevent="submitForm">
                      <div class="form-group">
                        <label for="name">姓名*</label>
                        <input type="text" id="name" v-model="form.name" required />
                      </div>
                      <div class="form-group">
                        <label for="email">郵件*</label>
                        <input type="email" id="email" v-model="form.email" required />
                      </div>
                      <div class="form-group">
                        <label for="phone">電話*</label>
                        <input type="tel" id="phone" v-model="form.phone" required />
                      </div>
                      <div class="form-group">
                        <label for="company">公司名稱*</label>
                        <input type="text" id="company" v-model="form.company" required />
                      </div>
                      <div class="form-group">
                        <label for="message">歡迎分享您對服務需求，以及期望如何應用至品牌</label>
                        <textarea id="message" v-model="form.message"></textarea>
                      </div>
                      <button type="submit" class="submit-button">Book a Demo</button>
                    </form>
                  </div>
            
              </div>
            </div>
       
  
        
  
        
 
  
      
    </div>
  </template>
  
  <style scoped lang="css">
  .content h1 {
    font-size: 2.5rem;
    font-weight: bold;
    margin-bottom: 0.5rem;
  }
  
  .content h2 {
    font-size: 2rem;
    font-weight: normal;
    margin-bottom: 1rem;
  }
  
  .content p {
    font-size: 1rem;
    margin-bottom: 2rem;
  }
  
  .content button {
    padding: 0.75rem 1.5rem;
    font-size: 1rem;
    color: white;
    background-color: black;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .content button:hover {
    background-color: #333;
  }
  </style>
  
  <script setup lang="ts">
  import "animate.css";
  import { ref } from 'vue';

const form = ref({
  name: '',
  email: '',
  phone: '',
  company: '',
  message: ''
});

const submitForm = () => {
  console.log('Form submitted', form.value);
};

  // interfaces & types & enums
  
  // props
  
  // emits
  
  // variables
  
  // computed properties
  
  // watches
  
  // methods
  
  // hooks
  
  
  </script>
  <style scoped lang="css">

  .form-container {
    background: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    width: 100%;
    max-width: 400px;
  }
  
  h1 {
    font-size: 2rem;
    font-weight: bold;
  }
  
  h2 {
    font-size: 1.5rem;
    text-align: center;
    margin-bottom: 20px;
  }
  
  p {
    font-size: 1rem;
    margin-top: 20px;
    color: #666;
  }
  
  .form-group {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
  }
  
  input,
  textarea {
    width: 100%;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
    box-sizing: border-box;
  }
  
  .submit-button {
    width: 100%;
    padding: 10px;
    border: none;
    border-radius: 5px;
    background: black;
    color: white;
    font-size: 1rem;
    cursor: pointer;
  }
  
  .submit-button:hover {
    background: #333;
  }
</style>
  