<script setup>
import axios from "axios";

axios.defaults.headers.common['X-Requested-With'] = 'XMLHttpRequest'
axios.defaults.headers.common['Accept'] = 'application/json'
axios.defaults.headers.common['Content-Type'] = 'application/json'
axios.defaults.baseURL = 'http://localhost:8000'
axios.defaults.withCredentials = true

async function register() {
  await axios.get('/sanctum/csrf-cookie')
  await axios.post('/register', {
    name: 'Valentin',
    email: 'test3@test.com',
    password: '123123123',
    password_confirmation: '123123123'
  })

  console.log('register done')
}

async function login() {
  await axios.get('/sanctum/csrf-cookie')
  await axios.post('/login', {
    email: 'test3@test.com',
    password: '123123123'
  })

  console.log('login done')
}
async function logout() {
  await axios.post('/logout')

  console.log('logout done')
}

async function getUser() {

  const user = await axios.get('/api/user')

  console.log('user data', user)
}

async function test() {
  const data = await axios.get('/api/test')

  console.log('test data', data)
}

</script>

<template>
  <button @click="register">Register</button>
  <button @click="login">login</button>
  <button @click="getUser">get user</button>
  <button @click="logout">logout</button>
  <button @click="test">test</button>

</template>

<style scoped>

</style>
