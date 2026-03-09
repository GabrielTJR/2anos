<script setup lang="ts">
import { Heart, Sparkles, Calendar, Star } from 'lucide-vue-next'

const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="bg-gradient-to-r from-rose-600 via-rose-500 to-rose-600 text-white">
    <!-- Decoração superior -->
    <div class="h-2 bg-gradient-to-r from-rose-300 via-rose-200 to-rose-300" />
    
    <div class="max-w-7xl mx-auto px-6 py-12">
      <div class="text-center">
        <!-- Ícones decorativos -->
        <div class="flex items-center justify-center gap-4 mb-6">
          <Sparkles class="w-5 h-5 text-rose-200 animate-float" style="animation-delay: 0s" />
          <Star class="w-4 h-4 text-rose-200 animate-float" style="animation-delay: 0.2s" />
          <Heart class="w-8 h-8 text-white fill-white animate-pulse-heart" />
          <Star class="w-4 h-4 text-rose-200 animate-float" style="animation-delay: 0.4s" />
          <Sparkles class="w-5 h-5 text-rose-200 animate-float" style="animation-delay: 0.6s" />
        </div>
        
        <!-- Mensagem principal -->
        <h3 class="text-2xl md:text-3xl font-serif font-semibold mb-4">
          2 Anos de Puro Amor
        </h3>
        
        <p class="text-rose-100 text-lg max-w-2xl mx-auto mb-6 leading-relaxed">
          Cada dia ao seu lado é uma bênção. Obrigado por fazer parte da minha vida 
          e por transformar momentos simples em memórias extraordinárias.
        </p>
        
        <!-- Data comemorativa -->
        <div class="inline-flex items-center gap-2 bg-white/20 backdrop-blur-sm px-6 py-3 rounded-full mb-8">
          <Calendar class="w-5 h-5" />
          <span class="font-medium">Comemorando desde 2024</span>
          <Heart class="w-4 h-4 fill-white" />
        </div>
        
        <!-- Frase romântica -->
        <div class="border-t border-rose-400/30 pt-8 mt-8">
          <p class="text-rose-200 italic font-serif text-lg mb-2">
            "Eu te amo não pelo que você é, mas pelo que eu sou quando estou com você."
          </p>
          <p class="text-rose-300 text-sm">— Roy Croft</p>
        </div>
        
        <!-- Corações decorativos -->
        <div class="flex items-center justify-center gap-2 mt-8">
          <span class="w-16 h-px bg-gradient-to-r from-transparent to-rose-300" />
          <Heart class="w-4 h-4 text-rose-300 fill-rose-300" />
          <Heart class="w-5 h-5 text-rose-200 fill-rose-200" />
          <Heart class="w-4 h-4 text-rose-300 fill-rose-300" />
          <span class="w-16 h-px bg-gradient-to-l from-transparent to-rose-300" />
        </div>
        
        <!-- Copyright -->
        <p class="text-rose-300 text-sm mt-6">
          Feito com 
          <Heart class="w-3 h-3 inline fill-rose-200 text-rose-200" /> 
          para celebrar nosso amor • {{ currentYear }}
        </p>
      </div>
    </div>
    
    <!-- Decoração inferior -->
    <div class="h-1 bg-gradient-to-r from-rose-700 via-rose-600 to-rose-700" />
  </footer>
</template>
