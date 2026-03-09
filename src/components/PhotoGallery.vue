<script setup lang="ts">
import { computed } from 'vue'
import { Camera, Heart, MapPin, Utensils, Laugh } from 'lucide-vue-next'

type Category = 'viagens' | 'comidas' | 'diversoes'

interface Props {
  category: Category
}

const props = defineProps<Props>()

interface PhotoItem {
  id: number
  imagem: string
  description: string
}

interface CategoryData {
  title: string
  subtitle: string
  icon: typeof Camera
  photos: PhotoItem[]
  emptyMessage: string
}

const categoryData: Record<Category, CategoryData> = {
  viagens: {
    title: 'Nossas Viagens',
    subtitle: 'Cada destino, uma nova história de amor',
    icon: MapPin,
    photos: [
      { id: 1, imagem: '/fotos/viagem0.jpeg', description: 'Nossa primeira viagem juntos' },
      { id: 2, imagem: '/fotos/viagem1.jpeg', description: 'A felicidade da piscina vazia' },
      { id: 3, imagem: '/fotos/viagem2.jpeg', description: 'O melhor café' },
      { id: 4, imagem: '/fotos/viagem3.jpeg', description: 'Devendo e Luxando' },
      { id: 5, imagem: '/fotos/viagem4.jpeg', description: 'Nosso pé na areia' },
      { id: 6, imagem: '/fotos/viagem5.jpeg', description: 'Mais um ano com você' },
    ],
    emptyMessage: 'Adicione fotos das suas viagens aqui!'
  },
  comidas: {
    title: 'Nossas Comidas',
    subtitle: 'O amor também passa pelo estômago',
    icon: Utensils,
    photos: [
      { id: 1, imagem: '/fotos/comida1.jpeg', description: 'Jantar com pizza e coberta' },
      { id: 2, imagem: '/fotos/comida2.jpeg', description: 'Adimirando a comida' },
      { id: 3, imagem: '/fotos/comida3.jpeg', description: 'Sem pausa para a foto' },
      { id: 4, imagem: '/fotos/comida4.jpeg', description: 'Pausa na viagem para comer' },
      { id: 5, imagem: '/fotos/comida5.jpeg', description: 'O cappuccino não pode faltar' },
      { id: 6, imagem: '/fotos/comida6.jpeg', description: 'Adora um almoço no shopping' },
    ],
    emptyMessage: 'Adicione fotos dos seus momentos gastronômicos!'
  },
  diversoes: {
    title: 'Nossas Diversões',
    subtitle: 'Risadas e momentos inesquecíveis',
    icon: Laugh,
    photos: [
      { id: 1, imagem: '/fotos/diversao0.jpeg', description: '23 aninhos da minha princesa' },
      { id: 2, imagem: '/fotos/diversao1.jpeg', description: 'Nosso primeiro show do Vintage' },
      { id: 3, imagem: '/fotos/diversao2.jpeg', description: 'Curtindo a marejada' },
      { id: 4, imagem: '/fotos/diversao3.jpeg', description: 'Natal juntinhos' },
      { id: 5, imagem: '/fotos/diversao4.jpeg', description: 'Conhecemos a Green Valey' },
      { id: 6, imagem: '/fotos/diversao5.jpeg', description: 'Minha meio biomédica' },
    ],
    emptyMessage: 'Adicione fotos das suas diversões!'
  }
}

const currentData = computed(() => categoryData[props.category])
</script>

<template>
  <section class="flex-1 p-6 lg:p-10">
    <div class="max-w-6xl mx-auto">
      <!-- Título da seção -->
      <div class="mb-8 animate-fade-in">
        <div class="flex items-center gap-3 mb-2">
          <component 
            :is="currentData.icon" 
            class="w-7 h-7 text-rose-500"
          />
          <h2 class="text-2xl md:text-3xl font-serif font-semibold text-rose-800">
            {{ currentData.title }}
          </h2>
        </div>
        <p class="text-rose-500/70 text-lg">{{ currentData.subtitle }}</p>
      </div>
      
      <!-- Grid de fotos -->
      <div class="photo-grid">
        <div
          v-for="(photo, index) in currentData.photos"
          :key="`${category}-${photo.id}`"
          class="photo-card animate-fade-in"
          :style="{ animationDelay: `${index * 0.1}s` }"
        >
          <div class="bg-white rounded-3xl overflow-hidden shadow-lg shadow-rose-100/50 border border-rose-100 group">
            <!-- Área da foto (imagem) -->
            <div class="aspect-[4/4] bg-gradient-to-br from-rose-50 via-blush to-rose-100 flex flex-col items-center justify-center relative overflow-hidden">
              <div class="absolute inset-0 bg-[radial-gradient(circle_at_30%_30%,rgba(253,164,175,0.3),transparent_50%)]" />
              
              <img :src="photo.imagem" alt="">
              
            </div>
            
            <!-- Descrição -->
            <div class="p-4 bg-white">
              <div class="flex items-center justify-between">
                <p class="text-rose-700 font-medium text-sm">{{ photo.description }}</p>
                <Heart class="w-4 h-4 text-rose-300 hover:text-rose-500 hover:fill-rose-500 cursor-pointer transition-colors" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
