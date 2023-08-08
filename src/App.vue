<script setup>

import { ref, reactive } from 'vue';


const loginForm = ref(true)

const registerForm = ref(false)

const userDashboard = ref(false)


const user = reactive({
  userName: '',
  password: ''
})

function openRegistration() {
  registerForm.value = true
  loginForm.value = false
}

function submit() {
  userDashboard.value = true
  registerForm.value = false
  loginForm.value = false
}


</script>


<template>
    <section class="flex h-screen w-full" :class="loginForm ? 'block' : 'hidden'">
      <div class="w-1/2"
        style="background-image: url(https://images.unsplash.com/photo-1690555575753-7aa27df96b52?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80); background-repeat: no-repeat; background-size: cover;">
        <h1 class="mb-5 text-2xl mt-10 ml-10 text-white">Kosmos!</h1>
      </div>
      <div class="w-1/2 flex flex-col justify-center items-center bg-gray-200">
        <h2 class="mb-5 text-xl">Login or register</h2>
        <div class="w-full max-w-xs">
          <form @submit.prevent="submit" class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
            <div class="mb-4">
              <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
                Username
              </label>
              <input
                class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                id="username" type="text" placeholder="Username">
            </div>
            <div class="mb-6">
              <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
                Password
              </label>
              <input
                class="shadow appearance-none border  rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
                id="password" type="password" placeholder="******************">
              <!-- <p class="text-red-500 text-xs italic">Please choose a password.</p> -->
            </div>
            <div class="flex items-center justify-between">
              <button
                class="bg-orange-600 hover:bg-orange-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
                type="submit">
                Sign In
              </button>
              <a class="inline-block align-baseline font-bold text-sm text-orange-600 hover:text-orange-800 cursor-pointer" @click="openRegistration()" >
                Or Register
              </a>
            </div>
          </form>
          <p class="text-center text-gray-500 text-xs">
            &copy;2023 Acme Corp. All rights reserved.
          </p>
        </div>
      </div>
    </section>

  <!-- Registration -->
    <section class="flex h-screen w-full" :class="registerForm ? 'block' : 'hidden'">
      <div class="w-1/2"
        style="background-image: url(https://images.unsplash.com/photo-1690555575753-7aa27df96b52?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80); background-repeat: no-repeat; background-size: cover;">
        <h1 class="mb-5 text-2xl mt-10 ml-10 text-white">Kosmos!</h1>
      </div>
      <div class="w-1/2 flex flex-col justify-center items-center bg-gray-200">
        <h2 class="mb-5 text-xl">Register</h2>
        <div class="w-full max-w-xs">
          <form @submit.prevent="submit" class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
            <div class="mb-4">
              <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
                Username
              </label>
              <input
                class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                id="username" type="text" placeholder="Username">
            </div>
            <div class="mb-6">
              <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
                Password
              </label>
              <input
                class="shadow appearance-none border  rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
                id="password" type="password" placeholder="******************">
              <!-- <p class="text-red-500 text-xs italic">Please choose a password.</p> -->
            </div>
            <div class="flex items-center justify-between">
              <button
                class="bg-orange-600 hover:bg-orange-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
                type="type">
                Register
              </button>
            </div>
          </form>
          <p class="text-center text-gray-500 text-xs">
            &copy;2023 Acme Corp. All rights reserved.
          </p>
        </div>
      </div>
    </section>

  <!-- Welcome Page -->
  <div :class="userDashboard ? 'block' : 'hidden'">
    <div class="flex min-h-screen flex-row bg-gray-100 text-gray-800">
      <aside
        class="sidebar w-48 -translate-x-full transform bg-white p-4 transition-transform duration-150 ease-in md:translate-x-0 md:shadow-md">
        <div class="my-4 w-full border-b-4 border-indigo-100 text-center">
          <span class="font-mono text-xl font-bold tracking-widest"> <span class="text-indigo-600">Welcome</span> {{
            user.name ? user.userName : "User" }}
          </span>
        </div>
        <div class="my-4"></div>
      </aside>
      <main class="main -ml-48 flex flex-grow flex-col p-4 transition-all duration-150 ease-in md:ml-0">
        <div class="flex h-full items-center justify-center bg-white text-center text-5xl font-bold shadow-md">
          {{ user.name ? user.userName : "User" }}
        </div>
      </main>
    </div>
  </div>
</template>
