<template>
  <div>
    <input type="text" v-model="text" />
    <button type="button" @click="send">按我</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const text = ref('')
const emit = defineEmits(['send-text'])
const send = () => {
  emit('send-text', text.value)
}
</script>
