<template>
  <div>
    <h2>註冊</h2>
    <input type="email" placeholder="email" v-model="signupField.email" />
    <input type="text" placeholder="password" v-model="signupField.password" />
    <input type="text" placeholder="nickname" v-model="signupField.nickname" />
    <button type="button" @click="signup">註冊</button>
    <br />
    {{ signupField }}
    UID:{{ signupRes }}
  </div>
  <div>
    <h2>登入</h2>
    <input type="email" placeholder="email" v-model="signInField.email" />
    <input type="text" placeholder="password" v-model="signInField.password" />
    <button type="button" @click="signIn">登入</button>
    <br />
    {{ signInField }}
    token: {{ signInRes }}
  </div>
  <div>
    <h2>驗證</h2>
    <div v-if="user.uid">
      <p>UID: {{ user.uid }}</p>
      <p>Nickname: {{ user.nickname }}</p>
    </div>
    <div v-else>你還沒有登入</div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import axios from 'axios'

const api_url = 'https://todolist-api.hexschool.io'

// 註冊
const signupField = ref({
  email: '',
  password: '',
  nickname: '',
})

const signupRes = ref('')

const signup = async () => {
  try {
    const res = await axios.post(`${api_url}/users/sign_up`, signupField.value)
    console.log(res)
    signupRes.value = res.data.uid
  } catch (error) {
    console.log(error)
  }
}

// 登入
const signInField = ref({
  email: '',
  password: '',
})

const signInRes = ref('')

const signIn = async () => {
  try {
    const res = await axios.post(`${api_url}/users/sign_in`, signInField.value)
    console.log(res)
    signInRes.value = res.data.token
    document.cookie = `customTodoToken=${res.data.token};path=/`
  } catch (error) {
    console.log(error)
  }
}

// 驗證
const user = ref({
  uid: '',
  nickname: '',
})
onMounted(async () => {
  const token = document.cookie.replace(/(?:^|.*;\s*)customTodoToken\s*=\s*([^;]*).*$/i, '$1')
  console.log(token)
  const res = await axios.get(`${api_url}/users/checkout`, {
    headers: {
      Authorization: token,
    },
  })
  console.log(res)
  user.value = res.data
})
</script>
