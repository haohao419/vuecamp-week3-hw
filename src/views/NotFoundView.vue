<template>
  <h1>此頁面404</h1>
  <h2>三秒後跳轉首頁...</h2>
</template>
<script setup>
import { useRouter } from 'vue-router'
const router = useRouter()

setTimeout(() => {
  router.push('/')
}, 3000)
</script>
