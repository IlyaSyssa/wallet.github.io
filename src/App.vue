<template>
  <img src="./components/icons/free-wallet-2844888-2365237.png" class="walletIcon" alt="Описание изображения">
  <div v-if="!isEditing" class="userName" @click="startEditing">{{ userName }}</div>
  <input v-else type="text" v-model="inputValue" @blur="finishEditing" @keyup.enter="finishEditing" class="userNameInput">
  <div class="balanceCard">
    <div class="grid-itemMoneyIcon">
      <img class="bagIcon" src="./components/icons/free-icon-money-bag-3359187.png"
    </div>
    <div class="grid-item">Balance {{  }}</div>
    <div class="grid-item">
        <div class="money%"></div>
    </div>
  </div>
  <hr class="lineUp">
  <div class="expence">
    Expence {{  }}
  </div>
  <div class="expenceTable">
    <div class="expence-item-grid"></div>
    <div class="expence-item-grid"></div>
    <div class="expence-item-grid"></div>
    <div class="expence-item-grid"></div>
    <div class="expence-item-grid"></div>
    <div class="expence-item-grid"></div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const userName = ref('Username');
const isEditing = ref(false);
const inputValue = ref(userName.value);

const startEditing = () => {
  isEditing.value = true;
  inputValue.value = userName.value;
};

const finishEditing = () => {
  isEditing.value = false;
  userName.value = inputValue.value;
};
</script>

<style>
.walletIcon {
  position: fixed;
  top: 10px;
  left: 15px;
  width: 73px;
}

.userName, .userNameInput {
  margin-left: 100px;
  margin-top: 35px;
  font-size: 20px;
}

.userName {
  cursor: pointer;
}

.userNameInput {
  font-size: 20px; 
}

.balanceCard {
  width: 422px;
  height: 84px;
  border-radius: 24px;
  background-color: #D9D9D9; /* Черный цвет с 50% прозрачности */
  
  /* Центрирование по горизонтали и выравнивание по вертикали с walletIcon */
  position: fixed;
  top: 10px; /* Уровень по вертикали с walletIcon */
  left: 50%;
  transform: translateX(-50%);

  /* CSS Grid */
  display: grid;
  grid-template-rows: 1fr; /* Одна строка, занимающая всю высоту */
  grid-template-columns: repeat(3, 1fr); /* Три столбца одинаковой ширины */
  /* Грид занимает всю высоту и ширину .balanceCard */
}

.grid-item, .grid-itemMoneyIcon {
  /* Визуальные стили для элементов внутри грида */
  display: flex;
  justify-content: center;
  align-items: center;
  color: rgb(0, 0, 0);
  font-size: 20px;
  border: none; /* Удаление границ для невидимых разделений */
}

.bagIcon {
  width: 67px;
}
.lineUp {
  position: relative;
  top: 35px;
 
}
.expence {
  width: 422px;
  height: 84px;
  border-radius: 24px;
  background-color: #D9D9D9; /* Цвет фона */
  position: fixed;
  top: 120px; /* Уровень по вертикали */
  left: 50%;
  transform: translateX(-50%);
  
  /* Flexbox для центрирования текста */
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 20px;
  text-align: center;
}
.expenceTable {
  width: 100%;
  height: 300px;
  background-color: #D9D9D9; /* Черный цвет с 50% прозрачности */
  
  /* Центрирование по горизонтали и выравнивание по вертикали с walletIcon */
  position: fixed;
  top: 250px; /* Уровень по вертикали с walletIcon */
  left: 50%;
  transform: translateX(-50%);

  /* CSS Grid */
  display: grid;
  grid-template-rows: 1fr; /* Одна строка, занимающая всю высоту */
  grid-template-columns: repeat(5, 1fr); /* Три столбца одинаковой ширины */
  /* Грид занимает всю высоту и ширину .balanceCard */
}
.expence-item-grid {

}
</style>
