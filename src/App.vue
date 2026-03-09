<script setup lang="ts">
import { ref } from 'vue'
import Sidebar from './components/Sidebar.vue'
import PhotoGallery from './components/PhotoGallery.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

type Category = 'viagens' | 'comidas' | 'diversoes'

const activeCategory = ref<Category>('viagens')

const handleCategoryChange = (category: Category) => {
  activeCategory.value = category
}
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <Header />
    
    <main class="flex-1 flex flex-col lg:flex-row">
      <Sidebar 
        :activeCategory="activeCategory" 
        @change-category="handleCategoryChange" 
      />
      
      <PhotoGallery :category="activeCategory" />
    </main>
    
    <Footer />
  </div>
</template>
