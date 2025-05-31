<script setup>
defineProps({
  item: Object,
});
</script>
<template>
  <router-link :to="{name: 'detail', params: { id: item.id } }">
    <img :src="item.src" alt="" />
    <h1>Модель: {{ item.brand }}</h1>
    <p>Цена: {{ item.price }}₽</p>
    <p>Размеры: {{ item.size }}</p>

    <div>
      <i class="far fa-star"></i>
      <p>{{ item.rating }}</p>
    </div>
  </router-link>
</template>

<style scoped>
div {
  display: flex;
  align-items: center;
}
img {
  aspect-ratio: 16/9;
  object-fit: cover;
}
a {
  width: 100%;
  padding: 30px;
  background: #696969;
  font-weight: bold;
  text-decoration: none;
  color: aliceblue;


}
h1 {
  font-size: 30px;
  font-family: 'Andale Mono', monospace;
  
}
p {
  font-size: 25px;
  font-family: 'Andale Mono', monospace;
}
i {
  color: yellow;
}
</style>


