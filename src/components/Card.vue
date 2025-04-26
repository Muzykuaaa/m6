<script setup>
defineProps({
  item: Object,
});
</script>
<template>
  <a>
    {{ item }}
    <img :src="item.img" alt="" />
    <h1>{{ item.title }}</h1>
    <p>{{ item.desc }}</p>
    <!-- <i v-if="item.like" class="fas fa-star"></i>
    <i v-else class="far fa-star"></i> -->
    <i class="fas fa-star" :class="item.like ? 'red' : 'black'"></i>
  </a>
</template>

<style scoped>
a {
  width: 500px;
  padding: 10px;
  background: #32383e;
}
.red {
    color: red;
}
.black{
    color: black;
}
</style>


