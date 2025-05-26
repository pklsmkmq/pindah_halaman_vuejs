<script setup>
const emit = defineEmits(['logout'])

const logout = () => {
  // Clear the logged-in user from localStorage
  localStorage.removeItem('loggedInUser')
  // Emit the logout event
  emit('logout', true)
}
</script>

<template>
  <h1>Home Component</h1>
  <button @click="logout"
    class="w-full bg-red-400 hover:bg-red-500 text-white font-semibold py-3 rounded-lg transition duration-200">Logout</button>
</template>
