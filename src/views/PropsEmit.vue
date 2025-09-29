<template>
  <div>
    {{ title }}
    <BaseCard @send-text="handleSendText" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import BaseCard from '@/components/BaseCard.vue'
const title = ref('原始標題')

const handleSendText = (txt) => {
  title.value = txt
}
</script>
