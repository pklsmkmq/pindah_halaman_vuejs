<script setup>

import { reactive, defineEmits } from 'vue'

const emit = defineEmits(['loginSuccess', 'register'])

const form = reactive({
    email: '',
    password: ''
})

const login = () => {
    const users = JSON.parse(localStorage.getItem('users')) || []

    // Cek apakah ada user yang cocok
    const foundUser = users.find(
        user => user.email === form.email && user.password === form.password
    )

    if (foundUser) {
        alert('Login berhasil!')
        localStorage.setItem('loggedInUser', JSON.stringify(foundUser))
        emit('loginSuccess', foundUser)
    } else {
        alert('Email atau password salah!')
    }

    // Reset form (opsional)
    form.email = ''
    form.password = ''
}

const regis = () => {
    // Arahkan ke halaman registrasi
    emit('register', true)
}
</script>

<template>
    <div class="min-h-screen w-[99vw] flex items-center justify-center bg-gradient-to-br from-sky-200 to-green-200">
        <div class="bg-white p-8 rounded-2xl shadow-lg w-full max-w-md">
            <h2 class="text-2xl font-bold mb-6 text-center text-gray-700">Login</h2>
            <form @submit.prevent="login" class="space-y-4">
                <input v-model="form.email" type="email" placeholder="Email"
                    class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-sky-300"
                    required />
                <input v-model="form.password" type="password" placeholder="Password"
                    class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-sky-300"
                    required />
                <button type="submit"
                    class="w-full bg-sky-400 hover:bg-sky-500 text-white font-semibold py-3 rounded-lg transition duration-200">
                    Login
                </button>
                <p class="text-center text-gray-600 mt-4">
                    Belum punya akun? <a @click.prevent="regis" class="text-sky-500 hover:underline">Daftar di sini</a>
                </p>
            </form>
        </div>
    </div>
</template>