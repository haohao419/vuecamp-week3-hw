<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <RouterLink to="/" class="add">Home</RouterLink>
  <RouterLink to="/about" class="add">About</RouterLink>
  <RouterLink to="/todo" class="add">Todo</RouterLink>
  <RouterLink to="/register" class="add">Register</RouterLink>
  <RouterLink to="/menu" class="add">Menu</RouterLink>
  <RouterLink to="/propsemit" class="add">PropsEmit</RouterLink>
  <RouterLink to="/test" class="add">Test</RouterLink>
  <RouterLink to="/item" class="add">Item</RouterLink>
  <RouterView />
</template>

<style>
.add {
  margin-right: 25px;
}
</style>
