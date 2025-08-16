<template>
    <h2>CRUD範例</h2>
    <input type="text" v-model="newName" placeholder="輸入品項名稱">
    {{ name }}
    <input type="number" name="" id="" v-model="newPrice" placeholder="輸入價格">
    {{ amount }}
    <button type="button" @click="addToProduct()">加入</button>
    <table>
        <thead>
            <tr>
                <th>品項</th>
                <th>價格</th>
                <th>調整價格</th>
                <th>刪除</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="item in data" :key="item.id">
                <td>{{ item.name }}</td>
                <td>{{ item.price }}</td>
                <td><input type="number" v-model="item.price"></td>
                <td><button type="button" @click="deleteProduct(item.id)">刪除此筆</button></td>
            </tr>
        </tbody>
    </table>
</template>
<script setup>

import { ref } from 'vue'

const newName = ref('')
const newPrice = ref(0)
const data = ref([
  { id: 1, name: "珍珠奶茶", price: 50 },
  { id: 2, name: "冬瓜檸檬", price: 45 },
  { id: 3, name: "翡翠檸檬", price: 55 },
  { id: 4, name: "四季春茶", price: 45 },
  { id: 5, name: "阿薩姆奶茶", price: 50 },
  { id: 6, name: "檸檬冰茶", price: 45 },
  { id: 7, name: "芒果綠茶", price: 55 },
  { id: 8, name: "抹茶拿鐵", price: 60 }
])

const addToProduct = () => {
    let newData = {
        id: new Date().getTime(),
        name: newName.value,
        price: newPrice.value
    }
    data.value.push(newData)
    newName.value = ''
    newPrice.value = 0
}

const deleteProduct = (id) => {
    let deleteIndex = data.value.findIndex(item => item.id === id)
    data.value.splice(deleteIndex, 1)
}

</script>
<style>
</style>