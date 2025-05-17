<script setup>
import Card from "../components/Card.vue";
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";

let route = useRoute();

let data = ref({});
let detail = ref();

async function getData() {
  let response = await fetch("https://ae51c2d080f15e19.mokky.dev/product");
  data.value = await response.json();
}
function getDataId() {
  for (let i of data.value) {
    if (i.id == route.params.id) {
      detail.value = i;
    }
  }
}

onMounted(async () => {
  await getData();
  await getDataId();
});
</script>

<template>
  <section v-if="detail">
        <nav>
            <img :src="detail.img" alt="" />
            <div class="demoFont">
                <h1>Модель: {{ detail.brand }}</h1>
                <p>Цена: {{ detail.price }}₽</p>
                <p>Размеры: {{ detail.size }}</p>
                <p class="desc">{{ detail.description }}</p>
            </div>
        </nav>
  </section>
</template>
<style scoped>

.desc{
    font-size: 15px;
}

img{
  aspect-ratio: 16/9;
  object-fit: cover;
  width: 25%;
  margin-top: 50px;
  border-radius: 11px;


}

nav{
    display: flex;
    justify-content: space-around;
    
    
}
section{
      background-color: aliceblue;
      height: 91vh;
}

div{
    margin: 75px;

    font-family: 'demoFont';
    line-height: 1.3;


}

.demoFont {
font-family: Georgia, serif;
font-size: 20px;
letter-spacing: 2px;
word-spacing: 2px;
color: #000000;
font-weight: 700;
text-decoration: none;
font-style: normal;
font-variant: small-caps;
text-transform: uppercase;
}
</style>