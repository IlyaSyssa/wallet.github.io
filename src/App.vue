<template>
  <img src="./components/icons/free-wallet-2844888-2365237.png" class="walletIcon" alt="Описание изображения">
  <div v-if="!isEditing" class="userName" @click="startEditing">{{ userName }}</div>
  <input v-else type="text" v-model="inputValue" @blur="finishEditing" @keyup.enter="finishEditing" class="userNameInput">
  <div class="balanceCard">
    <div class="grid-itemMoneyIcon">
      <img class="bagIcon" src="./components/icons/free-icon-money-bag-3359187.png">
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
    <div class="expence-item-grid1">
      <div class="expence-item-raw1">Food & Drink</div>
      <div class="expence-item-raw2"><img class="expence-png" src="./components/icons/free-icon-food-serving-3081078.png"></div>
      <div class="expence-item-raw3">{{  }}</div>
    </div>
    <div class="expence-item-grid2">
      <div class="expence-item-raw1">Transportation</div>
      <div class="expence-item-raw2"><img class="expence-png" src="./components/icons/free-icon-transportation-10183019.png"></div>
      <div class="expence-item-raw3">{{  }}</div>
    </div>
    <div class="expence-item-grid3">
      <div class="expence-item-raw1">Personal care</div>
      <div class="expence-item-raw2"><img class="expence-png" src="./components/icons/free-icon-care-8391984.png"></div>
      <div class="expence-item-raw3">{{  }}</div>
    </div>
    <div class="expence-item-grid4">
      <div class="expence-item-raw1">Shopping</div>
      <div class="expence-item-raw2"><img class="expence-png" src="./components/icons/free-icon-shopping-cart-1124198.png"></div>
      <div class="expence-item-raw3">{{  }}</div>
    </div>
    <div class="expence-item-grid5">
      <div class="expence-item-raw1"></div>
      <div class="expence-item-raw2">+</div>
      <div class="expence-item-raw3"></div>
    </div>
  </div>
  <div class="income">
    Income {{  }}
  </div>
  <div class="incomeTable">
    <div class="income-item-grid1">
      <div class="income-item-raw1">Food & Drink</div>
      <div class="income-item-raw2"><img class="expence-png" src="./components/icons/free-icon-food-serving-3081078.png"></div>
      <div class="income-item-raw3">{{  }}</div>
    </div>
    <div class="income-item-grid2">
      <div class="income-item-raw1">Transportation</div>
      <div class="income-item-raw2"><img class="expence-png" src="./components/icons/free-icon-transportation-10183019.png"></div>
      <div class="income-item-raw3">{{  }}</div>
    </div>
    <div class="income-item-grid3">
      <div class="income-item-raw1">Personal care</div>
      <div class="income-item-raw2"><img class="expence-png" src="./components/icons/free-icon-care-8391984.png"></div>
      <div class="income-item-raw3">{{  }}</div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';

const userName = ref('Username');
const isEditing = ref(false);
const inputValue = ref(userName.value);

// Восстанавливаем сохраненное имя пользователя при загрузке страницы
onMounted(() => {
  const savedUserName = localStorage.getItem('userName');
  if (savedUserName) {
    userName.value = savedUserName;
  }
});

const startEditing = () => {
  isEditing.value = true;
  inputValue.value = userName.value;
};

const finishEditing = () => {
  isEditing.value = false;
  userName.value = inputValue.value;
  // Сохраняем имя пользователя в localStorage
  localStorage.setItem('userName', userName.value);
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
  position: fixed;
}

.userName {
  cursor: pointer;
  position: fixed;
}

.userNameInput {
  font-size: 20px; 
  position: fixed;
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
  position: fixed;
            top: 95px;
            width: 100%;
            border: 1px solid black; 
 
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
 /* Черный цвет с 50% прозрачности */
  gap: 110px;
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
  display: flex;
  justify-content: center; 
}
.expence-item-grid1 {
  text-align: center;
  width: 225px;
  height: 225px;
  background-color: #FBFF45;
  border-radius: 24px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: rgb(0, 0, 0);
  font-size: 20px;
  border: none; /* Удаление границ для невидимых разделений */
  display: grid;
  grid-template-rows: repeat(3, 1fr);
  grid-template-columns: 1fr;
}
.expence-item-grid2 {
  text-align: center;
  width: 225px;
  height: 225px;
  background-color: #52A1FF;
  border-radius: 24px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: rgb(0, 0, 0);
  font-size: 20px;
  border: none; /* Удаление границ для невидимых разделений */
  display: grid;
  grid-template-rows: repeat(3, 1fr);
  grid-template-columns: 1fr;
}
.expence-item-grid3 {
  text-align: center;
  width: 225px;
  height: 225px;
  background-color: #B57AFF;
  border-radius: 24px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: rgb(0, 0, 0);
  font-size: 20px;
  border: none; /* Удаление границ для невидимых разделений */
  display: grid;
  grid-template-rows: repeat(3, 1fr);
  grid-template-columns: 1fr;
}
.expence-item-grid4 {
  text-align: center;
  width: 225px;
  height: 225px;
  background-color: #FF3232;
  border-radius: 24px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: rgb(0, 0, 0);
  font-size: 20px;
  border: none; /* Удаление границ для невидимых разделений */
  display: grid;
  grid-template-rows: repeat(3, 1fr);
  grid-template-columns: 1fr;
}
.expence-item-grid5 {
  text-align: center;
  width: 225px;
  height: 225px;
  background-color: #fcff4581;
  border-radius: 24px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: rgb(0, 0, 0);
  font-size: 20px;
  border: none; /* Удаление границ для невидимых разделений */
  display: grid;
  grid-template-rows: repeat(3, 1fr);
  grid-template-columns: 1fr;
}
.expence-png {
  width: 80px;
  height: 80px;
}
.income {
  width: 422px;
  height: 84px;
  border-radius: 24px;
  background-color: #D9D9D9; /* Цвет фона */
  position: fixed;
  top: 650px; /* Уровень по вертикали */
  left: 50%;
  transform: translateX(-50%);
  
  /* Flexbox для центрирования текста */
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 20px;
  text-align: center;
}
.incomeTable {
  width: 100%;
  height: 300px;
 /* Черный цвет с 50% прозрачности */
  gap: 110px;
  /* Центрирование по горизонтали и выравнивание по вертикали с walletIcon */
  position: fixed;
  top: 760px; /* Уровень по вертикали с walletIcon */
  left: 50%;
  transform: translateX(-50%);

  /* CSS Grid */
  display: grid;
  grid-template-rows: 1fr; /* Одна строка, занимающая всю высоту */
  grid-template-columns: repeat(5, 1fr); /* Три столбца одинаковой ширины */
  /* Грид занимает всю высоту и ширину .balanceCard */
  display: flex;
  justify-content: center; 
 
}
.income-item-grid1 {
  text-align: center;
  width: 449px;
  height: 112px;
  background-color: #45F2A9;
  border-radius: 24px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: rgb(0, 0, 0);
  font-size: 20px;
  border: none; /* Удаление границ для невидимых разделений */
  display: grid;
  grid-template-rows: 1fr;
  grid-template-columns: repeat(3, 1fr);
}
.income-item-grid2 {
  text-align: center;
  width: 449px;
  height: 112px;
  background-color: #61F55E;
  border-radius: 24px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: rgb(0, 0, 0);
  font-size: 20px;
  border: none; /* Удаление границ для невидимых разделений */
  display: grid;
  grid-template-rows: 1fr;
  grid-template-columns: repeat(3, 1fr);
}
.income-item-grid3 {
  text-align: center;
  width: 449px;
  height: 112px;
  background-color: #D9D9D9;
  border-radius: 24px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: rgb(0, 0, 0);
  font-size: 20px;
  border: none; /* Удаление границ для невидимых разделений */
  display: grid;
  grid-template-rows: 1fr;
  grid-template-columns: repeat(3, 1fr);
}
body, html {
            height: 100%;
            margin: 0;
            background: linear-gradient(to bottom, #BDC3C7, #2C3E50);
        }
</style>
