<script setup lang="ts">
import { Plane, UtensilsCrossed, PartyPopper, Sparkles } from 'lucide-vue-next'

type Category = 'viagens' | 'comidas' | 'diversoes'

interface Props {
  activeCategory: Category
}

defineProps<Props>()

const emit = defineEmits<{
  'change-category': [category: Category]
}>()


const categories = [
  { 
    id: 'viagens' as Category, 
    label: 'Nossas Viagens', 
    icon: Plane,
    description: 'Aventuras pelo mundo'
  },
  { 
    id: 'comidas' as Category, 
    label: 'Nossas Comidas', 
    icon: UtensilsCrossed,
    description: 'Sabores compartilhados'
  },
  { 
    id: 'diversoes' as Category, 
    label: 'Nossas Diversões', 
    icon: PartyPopper,
    description: 'Momentos de alegria'
  },
]
</script>

<template>
  <aside class="w-full lg:w-80 bg-white/50 backdrop-blur-sm border-r border-rose-100 p-6 lg:min-h-[calc(100vh-200px)]">
    <div class="flex items-center gap-2 mb-6">
      <Sparkles class="w-5 h-5 text-rose-400" />
      <h2 class="text-lg font-serif font-semibold text-rose-700">Nossas Memórias</h2>
    </div>
    
    <nav class="space-y-3">
      <button
        v-for="category in categories"
        :key="category.id"
        @click="emit('change-category', category.id)"
        :class="[
          'w-full flex items-center gap-4 p-4 rounded-2xl transition-all duration-300 text-left group',
          activeCategory === category.id
            ? 'bg-gradient-to-r from-rose-500 to-rose-400 text-white shadow-lg shadow-rose-200'
            : 'bg-white/70 hover:bg-white text-rose-700 hover:shadow-md border border-rose-100'
        ]"
      >
        <div
          :class="[
            'p-3 rounded-xl transition-all duration-300',
            activeCategory === category.id
              ? 'bg-white/20'
              : 'bg-rose-50 group-hover:bg-rose-100'
          ]"
        >
          <component 
            :is="category.icon" 
            :class="[
              'w-6 h-6 transition-colors',
              activeCategory === category.id ? 'text-white' : 'text-rose-500'
            ]"
          />
        </div>
        
        <div class="flex-1">
          <span 
            :class="[
              'block font-medium text-base',
              activeCategory === category.id ? 'text-white' : 'text-rose-800'
            ]"
          >
            {{ category.label }}
          </span>
          <span 
            :class="[
              'text-sm',
              activeCategory === category.id ? 'text-rose-100' : 'text-rose-400'
            ]"
          >
            {{ category.description }}
          </span>
        </div>
        
        <div
          v-if="activeCategory === category.id"
          class="w-2 h-2 rounded-full bg-white animate-pulse"
        />
      </button>
    </nav>
    
    <div v-if="activeCategory==='viagens'" class="mt-8 p-4 bg-gradient-to-br from-rose-50 to-blush rounded-2xl border border-rose-100">
      <p class="text-rose-600 text-sm text-center font-light italic">
        "Descobrir o mundo ao seu lado transforma qualquer caminho no melhor destino."
      </p>
      <p class="text-rose-400 text-xs text-center mt-2">— J. R. R. Tolkien</p>
    </div>

    <div v-else-if="activeCategory==='comidas'" class="mt-8 p-4 bg-gradient-to-br from-rose-50 to-blush rounded-2xl border border-rose-100">
      <p class="text-rose-600 text-sm text-center font-light italic">
        "A comida é simbólica do amor quando palavras são inadequadas."
      </p>
      <p class="text-rose-400 text-xs text-center mt-2">— Alan D. Wolfelt</p>
    </div>

    <div v-else class="mt-8 p-4 bg-gradient-to-br from-rose-50 to-blush rounded-2xl border border-rose-100">
      <p class="text-rose-600 text-sm text-center font-light italic">
        "Sei que o amor é real porque, ao seu lado, até os dias comuns viram festa."
      </p>
      <p class="text-rose-400 text-xs text-center mt-2">— Mario Quintana</p>
    </div>
  </aside>
</template>
