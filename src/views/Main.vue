<script setup>
import Card from "../components/Card.vue";
import { onMounted, ref } from "vue";


let data = ref({});

async function getData() {
  let response = await fetch("https://ae51c2d080f15e19.mokky.dev/product");
  data.value = await response.json();
}
onMounted(()=> {
  getData()
})

setInterval(() => {
  count.value++;
}, 500);
</script>
<template>
  <section>
    <Card v-for="(item, index) in data" :key="index" :item="item" />
  </section>
</template>

<style scoped>
section{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}
</style>
