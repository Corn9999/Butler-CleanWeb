<template>
  <div class="min-h-screen bg-cream flex flex-col justify-between selection:bg-navy selection:text-cream relative">
    
    <!-- Dust Sprite Easter Eggs -->
    <div 
      v-if="!sprite1Poofed"
      @click="poofSprite(1, $event)"
      class="fixed bottom-6 left-6 z-40 cursor-pointer transform hover:scale-110 active:scale-95 transition-all duration-300 hover:rotate-12 group"
      title="噢！一個灰塵小鬼！點擊清除它！"
    >
      <div class="relative animate-bounce" style="animation-duration: 3s;">
        <svg class="w-10 h-10 fill-navy text-navy drop-shadow-md transition-all duration-300 group-hover:fill-slate-700" viewBox="0 0 100 100">
          <path d="M 50 15 L 53 30 L 68 20 L 61 35 L 80 30 L 68 45 L 85 50 L 68 55 L 80 70 L 61 65 L 68 80 L 53 70 L 50 85 L 47 70 L 32 80 L 39 65 L 20 70 L 32 55 L 15 50 L 32 45 L 20 30 L 39 35 L 32 20 L 47 30 Z" />
          <circle cx="38" cy="48" r="10" fill="white" />
          <circle cx="38" cy="48" r="4.5" fill="black" />
          <circle cx="62" cy="48" r="10" fill="white" />
          <circle cx="62" cy="48" r="4.5" fill="black" />
        </svg>
        <span class="absolute -top-6 left-1/2 -translate-x-1/2 bg-navy text-cream text-[10px] px-2 py-0.5 rounded opacity-0 group-hover:opacity-100 transition-opacity duration-200 whitespace-nowrap shadow-sm">
          點我清除
        </span>
      </div>
    </div>
    
    <!-- Dust Sprite 2 -->
    <div 
      v-if="!sprite2Poofed"
      @click="poofSprite(2, $event)"
      class="fixed top-24 right-8 z-40 cursor-pointer transform hover:scale-110 active:scale-95 transition-all duration-300 hover:-rotate-12 group"
      title="這裡也有！點擊清除它！"
    >
      <div class="relative animate-pulse">
        <svg class="w-8 h-8 fill-navy text-navy drop-shadow-sm transition-all duration-300 group-hover:fill-slate-700" viewBox="0 0 100 100">
          <path d="M 50 15 L 53 30 L 68 20 L 61 35 L 80 30 L 68 45 L 85 50 L 68 55 L 80 70 L 61 65 L 68 80 L 53 70 L 50 85 L 47 70 L 32 80 L 39 65 L 20 70 L 32 55 L 15 50 L 32 45 L 20 30 L 39 35 L 32 20 L 47 30 Z" />
          <circle cx="38" cy="48" r="10" fill="white" />
          <circle cx="38" cy="47" r="4.5" fill="black" />
          <circle cx="62" cy="48" r="10" fill="white" />
          <circle cx="62" cy="47" r="4.5" fill="black" />
        </svg>
        <span class="absolute -top-6 left-1/2 -translate-x-1/2 bg-navy text-cream text-[10px] px-2 py-0.5 rounded opacity-0 group-hover:opacity-100 transition-opacity duration-200 whitespace-nowrap shadow-sm">
          掃除！
        </span>
      </div>
    </div>

    <!-- Poof Animation Particles Effect -->
    <div 
      v-if="poofEffect" 
      class="fixed z-50 pointer-events-none -translate-x-1/2 -translate-y-1/2" 
      :style="{ left: poofX + 'px', top: poofY + 'px' }"
    >
      <div class="animate-ping bg-navy/20 w-16 h-16 rounded-full flex items-center justify-center">
        <span class="text-xs text-navy font-bold">✨ Poof!</span>
      </div>
    </div>

    <!-- Header / Navbar -->
    <header class="border-b border-navy/10 sticky top-0 bg-cream/80 backdrop-blur-md z-30">
      <div class="max-w-6xl mx-auto px-6 py-4 flex justify-between items-center">
        <!-- Logo -->
        <router-link to="/" class="flex items-center space-x-2 group">
          <svg class="h-6 w-6 stroke-navy fill-none transition-transform duration-500 group-hover:rotate-6" stroke-width="2" viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
            <path d="m3 9 9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z" />
            <polyline points="9 22 9 12 15 12 15 22" />
          </svg>
          <span class="font-serif tracking-widest font-bold text-lg text-navy">MASTER HOUSE</span>
        </router-link>

        <!-- Navigation Menu -->
        <nav class="flex items-center space-x-8">
          <router-link 
            v-for="link in menuLinks" 
            :key="link.path" 
            :to="link.path"
            class="text-xs tracking-widest font-medium text-navy/70 hover:text-navy transition-colors duration-200 relative py-1 group"
          >
            {{ link.name }}
            <span class="absolute bottom-0 left-0 w-0 h-[2px] bg-navy transition-all duration-300 group-hover:w-full"></span>
            <!-- Active link dot/line -->
            <span v-if="$route.path === link.path" class="absolute bottom-0 left-0 w-full h-[2px] bg-navy"></span>
          </router-link>
        </nav>
      </div>
    </header>

    <!-- Main Content -->
    <main class="flex-grow max-w-6xl w-full mx-auto px-6 py-12 flex flex-col justify-center">
      <router-view v-slot="{ Component }">
        <transition name="fade" mode="out-in">
          <component :is="Component" />
        </transition>
      </router-view>
    </main>

    <!-- Footer -->
    <footer class="border-t border-navy/10 py-8">
      <div class="max-w-6xl mx-auto px-6 flex flex-col md:flex-row justify-between items-center text-xs text-navy/50 tracking-wider">
        <p>&copy; 2026 MASTER HOUSE. ALL RIGHTS RESERVED.</p>
        <div class="flex space-x-6 mt-4 md:mt-0">
          <a href="#" class="hover:text-navy transition-colors">INSTAGRAM</a>
          <a href="#" class="hover:text-navy transition-colors">LINKEDIN</a>
          <a href="#" class="hover:text-navy transition-colors">TWITTER</a>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const menuLinks = [
  { name: 'HOME', path: '/' },
  { name: 'CONTACT', path: '/contact' },
  { name: 'INFO', path: '/info' }
]

const sprite1Poofed = ref(false)
const sprite2Poofed = ref(false)

const poofEffect = ref(false)
const poofX = ref(0)
const poofY = ref(0)

const poofSprite = (num, event) => {
  if (num === 1) sprite1Poofed.value = true
  if (num === 2) sprite2Poofed.value = true
  
  poofX.value = event.clientX
  poofY.value = event.clientY
  poofEffect.value = true
  
  setTimeout(() => {
    poofEffect.value = false
  }, 600)
}
</script>
