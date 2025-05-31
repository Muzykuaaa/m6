<script setup></script>

<template>
  <header>
    <router-link to="/">Главная</router-link>
    <router-link to="/faq">Вопросы</router-link>
    <router-link to="/admin">Админ Панель</router-link>
  </header>
</template>



<style scoped>
header{
  background-color: #ADD8E6;
  display: flex;
  justify-content: space-evenly;
  padding: 20px;
  font-family: 'Andale Mono', monospace;
  font-size: 23px;

}
.router-link-active {
  color: #E0FFFF;
}
a {
  text-decoration: none;
  color: #4682B4;
  background-color: #B0C4DE;
  padding: 7px;
  border-radius: 14px;
  
}

</style>
