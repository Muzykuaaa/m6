<script setup>
import {ref } from "vue";

let data = [
  {
    quest: "1.Как сделать заказ?",
    answer: "Вы можете оформить заказ через наш сайт, выбрав нужный товар и заполнив форму с контактной информацией. После подтверждения — мы свяжемся с вами.",
  },
  {
    quest: "2.Сколько времени занимает доставка?",
    answer: "Сроки доставки зависят от вашего региона. В среднем, доставка по городу занимает 1–3 рабочих дня, по стране — до 7 дней.",
  },
  {
    quest: "3.Можно ли изменить заказ после оформления?",
    answer: "Чтобы изменить заказ после оформления надо обратиться в службу поддержки",
  },
  {
    quest: "4.Как обратиться в службу поддержки?",
    answer: "Обратиться электронным письмом на почту Google@gmail.com",
  }
];
let ans_active = ref(0);

</script>

<template>
  <section>
    <div v-for="(item, index) in data" :key="index">
        <div class="faq">
            <nav>
                <h1>
                    {{item.quest}}
                </h1>
                <i class="fas fa-plus" @click="ans_active=index"></i>

            </nav>
            <p :class="{'active': ans_active==index}">
                {{item.answer}}
            </p>
        </div>
    </div>
  </section>
</template>
<style scoped>
    
    section {
        
    }

    div {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        margin: 10px;
    }
    .faq {
        border: 1px solid black;
        border-radius: 15px;
    }
    nav {
        display: flex;

        align-items: center;
        justify-content: space-between;
        padding: 2px;
    }

    h1 {
        font-size: 30px;
        padding-left: 20px;

    }

    i {
        font-size: 20px;
        padding-right: 20px;


    }
    p {
        font-size: 27px;
        padding: 3px;
        padding-left: 20px;
        max-height: 0px;
        overflow: hidden;
        transition: 2s;
    }

    .active {
        max-height: 400px;
    }
</style>
