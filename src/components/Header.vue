<script setup lang="ts">
import { Heart } from 'lucide-vue-next'
</script>

<template>
  <header class="bg-white/70 backdrop-blur-md border-b border-rose-100 sticky top-0 z-50">
    <div class="max-w-7xl mx-auto px-6 py-6">
      <div class="flex flex-col items-center justify-center text-center">
        <div class="flex items-center gap-3 mb-3">
          <Heart class="w-8 h-8 text-rose-500 animate-pulse-heart fill-rose-500" />
          <h1 class="text-3xl md:text-4xl lg:text-5xl font-serif font-semibold text-rose-800">
            2 Anos de Amor
          </h1>
          <Heart class="w-8 h-8 text-rose-500 animate-pulse-heart fill-rose-500" />
        </div>
        
        <p class="text-rose-600/80 text-lg md:text-xl font-light tracking-wide">
          Cada momento ao seu lado é uma história que guardo no coração
        </p>
        
        <div class="flex items-center gap-2 mt-4">
          <span class="w-12 h-px bg-gradient-to-r from-transparent via-rose-300 to-transparent"></span>
          <span class="text-rose-400 text-sm font-medium">Nossa Jornada Juntos</span>
          <span class="w-12 h-px bg-gradient-to-r from-transparent via-rose-300 to-transparent"></span>
        </div>
      </div>
    </div>
  </header>
</template>
