<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <RouterLink to="/">Home</RouterLink>
  <RouterLink to="/about">About</RouterLink>
  <RouterLink to="/todo">Todo</RouterLink>
  <RouterLink to="/register">Register</RouterLink>
  <RouterLink to="/menu">menu</RouterLink>
  <RouterView />
</template>

