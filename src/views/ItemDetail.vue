<template>
    <h2>產品詳細編號{{ id }}</h2>
    {{ person }}
</template>

<script setup>
    import { useRoute } from 'vue-router'
    import { ref, onMounted } from 'vue'
    const route = useRoute()
    const { id } = route.params

    import axios from 'axios'
    const person = ref('')
    onMounted(async ()=> {
        const data = await axios.get(`https://randomuser.me/api?seed=${id}`)

        console.log(data.data.results)
        person.value = data.data.results
    })


</script>