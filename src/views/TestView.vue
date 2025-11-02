<template>
  <div>
    <h1>我是測試頁面123</h1>
    <nav>
      <RouterLink to="/test/message">訊息頁面</RouterLink> |
      <RouterLink to="/test/product">商品頁面</RouterLink>
    </nav>
    <RouterView />
  </div>
</template>

<script setup>
import { RouterView, RouterLink } from 'vue-router'
</script>
