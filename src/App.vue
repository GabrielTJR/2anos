<script setup lang="ts">
import { ref } from 'vue'
import Sidebar from './components/Sidebar.vue'
import PhotoGallery from './components/PhotoGallery.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import { computed } from 'vue'

type Category = 'viagens' | 'comidas' | 'diversoes'

const activeCategory = ref<Category>('viagens')

const handleCategoryChange = (category: Category) => {
  activeCategory.value = category
}
const categories: Category[] = ['viagens', 'comidas', 'diversoes']

const sidebarRef = ref()

const nextCategory = () => {
  const currentIndex = categories.indexOf(activeCategory.value)
  const nextIndex = (currentIndex + 1) % categories.length

  activeCategory.value = categories[nextIndex]

  sidebarRef.value?.$el.scrollIntoView({
    behavior: 'smooth'
  })
}

const categoryNames: Record<Category, string> = {
  viagens: 'Viagens',
  comidas: 'Comidas',
  diversoes: 'Diversões'
}

const nextCategoryLabel = computed(() => {
  const currentIndex = categories.indexOf(activeCategory.value)
  const nextIndex = (currentIndex + 1) % categories.length
  return categoryNames[categories[nextIndex]]
})

const isLastCategory = computed(() => {
  return activeCategory.value === 'diversoes'
})
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <Header />
    
    <main class="flex-1 flex flex-col lg:flex-row">
      <Sidebar 
        ref="sidebarRef"
        :activeCategory="activeCategory" 
        @change-category="handleCategoryChange" 
      />
      
      <div class="flex-1 flex flex-col">
        <PhotoGallery :category="activeCategory" /> <br>
        
        <div class="flex justify-center my-8">
            <button
              v-if="!isLastCategory"
              @click="nextCategory"
              class="px-6 py-3 rounded-2xl bg-gradient-to-r from-rose-500 to-rose-400 text-white font-medium shadow-lg shadow-rose-200 hover:scale-105 hover:shadow-xl transition-all duration-300"
            >
              Próximo Tema: {{ nextCategoryLabel }}
            </button>

            <span v-else class="text-rose-500">
              Eu te amo ❤️
            </span>
        </div>
      </div>
    </main>
    
    <Footer />
  </div>
</template>
