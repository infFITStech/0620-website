<template>
    <div>
        <div class="inf-fits-benefits">
            <div class="benefit-row" v-for="(row, rowIndex) in cardRows" :key="rowIndex">
              <div
                class="benefit py-20 px-10"
                :class="{'highlight': rowIndex === 0 && index === 0, 'gray': (rowIndex === 0 && index === 2)||(rowIndex === 1 && index === 0), 'yellow':( rowIndex === 0 && index === 1)||(rowIndex === 1 && index === 2)}"
                v-for="(card, index) in row"
                :key="index"
                style="border:1px solid #1c1c1c; border-top-color:transparent;"
                :style="{ borderRightColor: index === 2||index===0 ? 'transparent' : ' #1c1c1c' , borderLeftColor: index===0||index===2?'transparent':'#1c1c1c'}"

              >
                <h3 class="mb-11">{{ card.title }}</h3>
                <p>{{ card.body }}</p>
              </div>
            </div>
          </div>
    </div>
  </template>
  
  <script setup lang="ts">
import { computed } from 'vue';
import { useI18n } from 'vue-i18n';

const { tm, locale } = useI18n();

const cardRows = computed(() => {
  const cards:Object[] = tm('components.default.home.infBenefits.cards');
  const rows = [];
  console.log(cards, "cardsssss")
  for (let i = 0; i < cards.length; i += 3) {
    rows.push(cards.slice(i, i + 3));
  }
  return rows;
});
  </script>
  <style scoped lang="css">
  .inf-fits-benefits {
    display: flex;
    flex-wrap: wrap;
    width: 100%;
    box-sizing: border-box;
    border-top:1px solid #1c1c1c;
  }
  
  .benefit-row {
    display: flex;
    width: 100%;

  }
  
  .benefit {
    flex: 1;
    box-sizing: border-box;
    text-align: center;
    height: 500px;
    

  }
  
  .benefit h3 {
    font-size: 36px;
  }
  
  .benefit p {
    font-size: 1em;
    line-height: 1.5;
  }
  
  .highlight {
    background-color: #414141;
    color: #ffffff;
  }
  
  .gray {
    background-color: #f5f5f5;
  }
  
  .yellow {
    background-color: #f7f6e7;
  }
  </style>