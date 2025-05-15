<script setup>
import { ref } from 'vue'
import HomeComponent from './components/HomeComp.vue'
import ProductComponent from './components/ProductComp.vue'
import BlogComponent from './components/BlogComp.vue'
import ProfilComponent from './components/ProfilComp.vue'
import ContactComponent from './components/ContactComp.vue'

const url = ref('Home')

const gantiUrl = (value) => {
  url.value = value
  console.log(url.value)
}
</script>

<template>
  <div class="flex justify-center gap-5 py-3">
    <ul class="flex gap-5">
      <li><a href="#" @click.prevent="gantiUrl('Home')">Home</a></li>
      <li><a href="#" @click.prevent="gantiUrl('Product')">Product</a></li>
      <li><a href="#" @click.prevent="gantiUrl('Blog')">Blog</a></li>
      <li><a href="#" @click.prevent="gantiUrl('Profil')">Profil</a></li>
      <li><a href="#" @click.prevent="gantiUrl('Contact')">Contact</a></li>
    </ul>
  </div>

  <div class="w-full min-h-[90vh] flex items-center justify-center">
    <div v-if="url === 'Home'">
      <HomeComponent />
    </div>

    <div v-if="url === 'Product'">
      <ProductComponent />
    </div>

    <div v-if="url === 'Blog'">
      <BlogComponent />
    </div>

    <div v-if="url === 'Profil'">
      <ProfilComponent />
    </div>

    <div v-if="url === 'Contact'">
      <ContactComponent />
    </div>
  </div>
</template>

<style scoped></style>
