<script setup>
import { ref } from "vue";

const bankCount = ref(0);
const counter = ref(0);

const clickHandler = (num) => {
  bankCount.value += num;
  counter.value++;
}

const resetHandler = () => {
  counter.value = 0;
  bankCount.value = 0;
}

const data = [
  {
    date: "1 ноября",
    text: "Въезжаем и платим 600$ за месяц + 600$ в счет последнего месяца",
    plus: 600,
    buttonText: "К декабрю ⏭️"
  },
  {
    date: "1 декабря",
    text: "Платим 600$ за месяц",
    plus: 0,
    buttonText: "К январю ⏭️"
  },
  {
    date: "1 января",
    text: "Платим 600$ за месяц",
    plus: 0,
    buttonText: "К февралю ⏭️"
  },
  {
    date: "1 февраля",
    text: "Платим 600$ за месяц",
    plus: 0,
    buttonText: "К марту ⏭️"
  },
  {
    date: "1 марта",
    text: "Платим 600$ за месяц",
    plus: 0,
    buttonText: "К апрелю ⏭️"
  },
  {
    date: "1 апреля",
    text: "Платим 600$ за месяц",
    plus: 0,
    buttonText: "К маю ⏭️"
  },
  {
    date: "1 мая",
    text: "Платим 600$ за месяц + 50$ в счет последнего месяца (Есть в переписке)",
    plus: 50,
    buttonText: "К июню ⏭️"
  },
  {
    date: "1 июня",
    text: "Платим 650$ за месяц",
    plus: 0,
    buttonText: "К июлю ⏭️"
  },
  {
    date: "1 июля",
    text: "Платим 650$ за месяц",
    plus: 0,
    buttonText: "К августу ⏭️"
  },
  {
    date: "примерно 5 августа",
    text: "Вы последний раз заезжаете за деньгами, мы платим 650$ за месяц",
    plus: 0,
    buttonText: "К сентябрю ⏭️"
  },
  {
    date: "1 сентября",
    text: 'Мы не платим, этот месяц по идее должен быть снова 600$. А теперь смотрим на "счет" последнего месяца, сколько же там?',
    plus: 0,
    buttonText: "Вернуться к началу и пройтись еще раз ⏪",
    toStart: true
  }
]
</script>

<template>
  <div>
    <div class="bank">
      "Счет" последнего месяца:
      <span>
        {{ bankCount }}$
      </span>
    </div>
    <div v-if="data[counter]">
      <h3>
        {{ data[counter].date }}
      </h3>
      <p>
        {{ data[counter].text }}
      </p>
      <button v-if="!data[counter].toStart" @click="clickHandler(data[counter].plus)">
        {{ data[counter].buttonText }}
      </button>
      <button v-else @click="resetHandler">
        {{ data[counter].buttonText }}
      </button>
    </div>
  </div>
</template>

<style scoped>
.bank {
  font-size: 20px;
}
.bank span {
  display: inline-block;
  width: 80px;
  padding: 5px;
  margin-left: 10px;
  text-decoration: underline;
  font-weight: bold;
  border: 2px solid #fff;
}
p {
  font-size: 18px;
}
button {
  color: #fff;
  width: 220px;
  text-transform: uppercase;
  border: 2px solid #fff;
}
</style>
