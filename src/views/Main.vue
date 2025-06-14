<script setup>
import Card from "../components/Card.vue";
import { onMounted, ref } from "vue";

import Loader from "../components/Loader.vue" //


let data = ref([]);

async function getData() {
  let response = await fetch("https://ae51c2d080f15e19.mokky.dev/product");
  data.value = await response.json();
}

let sortValue = ref("")

function sortData() {
  console.log(data.value);
  if (sortValue.value == "up") {
  data.value.sort((a,b) => {
    return a.price - b.price
  });
  } else if (sortValue.value == "down") {
    data.value.sort((a, b) => {
      return b.price - a.price;
    });
  }
  
   data.value = newData;
   console.log(data.value)
}

let search = ref("")

async function searchData() {
  await getData();
  search.value = search.value.trim().toLowerCase();
  data.value = data.value.filter((item) => {
    return item.brand.toLowerCase().includes(search.value) || item.description.toLowerCase().includes(search.value); 
});
}

onMounted(()=> {
  getData()
})


</script>
<template>
  <section>
    <Loader v-if="data.length == 0" />
    <nav>
      <label>
        <p>Сортировка:</p>
        <select v-model="sortValue" @change="sortData">
            <option value="up">По возврастанию цены</option>
            <option value="down">По убыванию цены</option>
        </select>
      </label>
      <label>
        <p>Поиск:</p>
        <input v-model="search" @change="searchData"/>
        
      </label>
      {{ sortValue }}
    </nav>
      <div>
        <Card v-for="(item, index) in data" :key="index" :item="item" />
      </div>
  </section>
</template>

<style scoped>
input{
  
}
nav {
  display: flex;
  justify-content: center;
  gap: 50px;
  margin: 50px 0;
}
label {
  display: flex;
}
div{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 30px;
  margin: 30px;
}
</style>
