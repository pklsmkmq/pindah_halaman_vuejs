<script setup>
import { reactive, defineEmits } from 'vue'

const form = reactive({
    name: '',
    email: '',
    password: ''
})

const emit = defineEmits(['back'])

const register = () => {
    const users = JSON.parse(localStorage.getItem('users')) || []

    users.push({
        name: form.name,
        email: form.email,
        password: form.password
    })

    localStorage.setItem('users', JSON.stringify(users))

    alert('Registrasi berhasil!')

    form.name = ''
    form.email = ''
    form.password = ''
}

const login = () => {
    // Arahkan ke halaman login
    emit('back', true)
}
</script>

<template>
    <div class="min-h-screen w-[99vw] flex items-center justify-center bg-gradient-to-br from-sky-200 to-green-200">
        <div class="bg-white p-8 rounded-2xl shadow-lg w-full max-w-md">
            <h2 class="text-2xl font-bold mb-6 text-center text-gray-700">Form Registrasi</h2>
            <form @submit.prevent="register" class="space-y-4">
                <input v-model="form.name" type="text" placeholder="Nama"
                    class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-green-300"
                    required />
                <input v-model="form.email" type="email" placeholder="Email"
                    class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-green-300"
                    required />
                <input v-model="form.password" type="password" placeholder="Password"
                    class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-green-300"
                    required />
                <button type="submit"
                    class="w-full bg-green-400 hover:bg-green-500 text-white font-semibold py-3 rounded-lg transition duration-200">
                    Daftar
                </button>
                <p class="text-center text-gray-600 mt-4">
                    Kembali ke halaman <a @click.prevent="login" class="text-sky-500 hover:underline">Login</a>
                </p>
            </form>
        </div>
    </div>
</template>