<script setup>
import Header from "./components/Header.vue";
import { RouterView } from "vue-router"
</script>

<template>
  <main>
    <Header />
    <RouterView />
  </main>
</template>

<style scoped></style>
