<script setup>
import Card from "../components/Card.vue";
import { ref } from "vue";

let count = ref(8)


let data = [
    {
        img: "ссылка",
        title: "назв",
        desc: "Опис",
        like: true
    },
        {
        img: "ссылка",
        title: "назв1",
        desc: "Опис1",
        like: false
    }
]

setInterval(() => {
    count.value++;
}, 500);
</script>
<template>
  <section>
    {{ count }}
    <Card v-for="(item, index) in data" :key="index" :item="item"/>

  </section>
</template>

<style scoped></style>
