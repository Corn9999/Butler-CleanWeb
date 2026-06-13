<template>
  <div class="flex flex-col lg:flex-row items-center justify-between gap-8 lg:gap-12 py-2 min-h-[calc(100vh-180px)] max-h-screen overflow-hidden">
    
    <!-- Left Column: Copywriting & CTA -->
    <div class="w-full lg:w-[42%] text-center lg:text-left space-y-5 max-w-md shrink-0">
      <div class="space-y-1">
        <span class="text-[10px] tracking-[0.25em] text-dust font-bold uppercase block">Premium Custodian Service</span>
        <h1 class="text-2xl md:text-3xl lg:text-4xl font-serif text-navy font-bold tracking-widest leading-normal">
          以秩序為名的服務
        </h1>
      </div>
      
      <p class="text-xs md:text-sm text-navy/60 leading-relaxed tracking-wider font-light">
        您的守護者，您的清潔專家。我們以最嚴格的工藝標準與有條不紊的紀律，為您的起居空間重新注入純淨與秩序。請扮演「管家」，在右側客廳找出髒污並選擇工具清除。
      </p>

      <div class="pt-2 flex flex-col sm:flex-row gap-3 justify-center lg:justify-start">
        <router-link 
          to="/contact" 
          class="btn-premium px-6 py-3 bg-oatmeal text-navy font-medium text-[11px] tracking-widest uppercase rounded border border-navy/10 hover:bg-oatmeal-dark text-center"
        >
          預約您的服務
        </router-link>
        <router-link 
          to="/info" 
          class="btn-premium px-6 py-3 bg-white text-navy font-medium text-[11px] tracking-widest uppercase rounded border border-navy/20 hover:border-navy hover:bg-navy/5 text-center"
        >
          查看服務指南
        </router-link>
      </div>
      
      <!-- Trust Indicator -->
      <div class="pt-4 border-t border-navy/5 flex items-center justify-center lg:justify-start space-x-4 text-[9px] tracking-widest text-navy/40 font-semibold uppercase">
        <div class="flex items-center space-x-1">
          <svg class="w-3.5 h-3.5 stroke-navy/40 fill-none" stroke-width="2" viewBox="0 0 24 24"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
          <span>100% 滿意保證</span>
        </div>
        <div class="flex items-center space-x-1">
          <svg class="w-3.5 h-3.5 stroke-navy/40 fill-none" stroke-width="2" viewBox="0 0 24 24"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"/><polyline points="22 4 12 14.01 9 11.01"/></svg>
          <span>管家級工法</span>
        </div>
      </div>
    </div>

    <!-- Right Column: Compact Interactive Mini-Game Workspace (Spot the Dirt Style) -->
    <div class="w-full lg:w-[58%] flex flex-col justify-center items-center select-none relative max-w-[500px] lg:max-w-none">
      
      <!-- Game Container -->
      <div class="w-full bg-white border border-navy/10 rounded-lg p-4 shadow-sm flex flex-col space-y-3 relative overflow-hidden">
        
        <!-- Game Header -->
        <div class="flex justify-between items-center border-b border-navy/5 pb-2">
          <span class="text-[10px] tracking-wider text-navy/40 font-bold uppercase">大家來找碴：客廳除垢</span>
          <div class="flex items-center space-x-2">
            <span class="text-[9px] tracking-wider text-navy/60 font-semibold">
              清理進度: {{ completedCount }}/4
            </span>
            <div class="w-16 h-1 bg-navy/10 rounded-full overflow-hidden">
              <div 
                class="h-full bg-navy transition-all duration-500" 
                :style="{ width: `${(completedCount / 4) * 100}%` }"
              ></div>
            </div>
          </div>
        </div>

        <!-- Chores Checklist -->
        <div class="grid grid-cols-2 gap-2 bg-cream/40 p-2 rounded border border-navy/5 text-[9px] font-bold tracking-wider">
          <div 
            v-for="chore in chores" 
            :key="chore.id"
            class="flex items-center space-x-1.5 transition-colors duration-300"
            :class="chore.completed ? 'text-navy/40' : 'text-navy'"
          >
            <span 
              class="w-3.5 h-3.5 rounded flex items-center justify-center text-[8px] border transition-all duration-300"
              :class="[
                chore.completed 
                  ? 'bg-emerald-500 text-white border-emerald-500' 
                  : 'bg-white border-navy/20'
              ]"
            >
              <span v-if="chore.completed">✓</span>
            </span>
            <span :class="{ 'line-through decoration-navy/20': chore.completed }">{{ chore.name }}</span>
          </div>
        </div>

        <!-- Interactive Canvas + Tool Workspace -->
        <div class="flex gap-3 items-stretch relative min-h-[220px]">
          
          <!-- Canvas Layer Container -->
          <div class="flex-grow aspect-[4/3] bg-cream/10 rounded border border-navy/5 relative overflow-hidden flex items-center justify-center">
            
            <!-- 1. Background SVG: Living Room Setup -->
            <div class="absolute inset-0 flex items-center justify-center pointer-events-none z-0">
              <svg class="w-full h-full p-2" viewBox="0 0 400 300" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect width="400" height="300" rx="6" fill="#FAF8F5"/>
                <!-- Wall board lines -->
                <line x1="0" y1="200" x2="400" y2="200" stroke="#F1F5F9" stroke-width="2"/>
                
                <!-- Cabinet (Left Side Chores) -->
                <rect x="50" y="130" width="100" height="100" rx="2" fill="#C29B78" stroke="#9A7B5C" stroke-width="2"/>
                <rect x="45" y="125" width="110" height="6" rx="1" fill="#D2A984" stroke="#9A7B5C" stroke-width="1.5"/>
                <line x1="100" y1="130" x2="100" y2="230" stroke="#9A7B5C" stroke-width="1.5"/>
                <circle cx="75" cy="180" r="3" fill="#475569"/>
                <circle cx="125" cy="180" r="3" fill="#475569"/>
                
                <!-- Coffee Table (Right Side Chores) -->
                <rect x="230" y="160" width="120" height="40" rx="2" fill="#E2E8F0" stroke="#CBD5E1" stroke-width="2"/>
                <line x1="250" y1="200" x2="250" y2="230" stroke="#CBD5E1" stroke-width="3"/>
                <line x1="330" y1="200" x2="330" y2="230" stroke="#CBD5E1" stroke-width="3"/>

                <!-- Floor Carpet Rug (Bottom Center Chores) -->
                <ellipse cx="200" cy="245" rx="130" ry="30" fill="#FAF8F5" stroke="#E2E8F0" stroke-width="1.5"/>
                
                <!-- Clean Sparkles -->
                <g v-if="gameCompleted" class="sparkle-anim">
                  <path d="M 280 80 L 283 83 L 280 86 L 277 83 Z" fill="#D2A984" />
                  <path d="M 80 100 L 83 103 L 80 106 L 77 103 Z" fill="#D2A984" />
                </g>
              </svg>
            </div>

            <!-- 2. Floor Stain Canvas Layer (Mop) -->
            <canvas 
              ref="stainCanvasRef" 
              class="absolute inset-0 w-full h-full pointer-events-none z-10" 
              width="400" 
              height="300"
            ></canvas>

            <!-- 3. Floor Dust Canvas Layer (Vacuum) -->
            <canvas 
              ref="dustCanvasRef" 
              class="absolute inset-0 w-full h-full pointer-events-none z-12" 
              width="400" 
              height="300"
            ></canvas>

            <!-- 4. Cabinet Stain Canvas Layer (Cloth) -->
            <canvas 
              ref="cabinetCanvasRef" 
              class="absolute inset-0 w-full h-full pointer-events-none z-14" 
              width="400" 
              height="300"
            ></canvas>

            <!-- 5. Interactive Clickable Trash Items (DOM Overlays) -->
            <div 
              v-for="(t, idx) in trashItems" 
              :key="idx"
              v-show="!t.collected"
              @click="collectTrash(idx)"
              class="absolute w-6 h-6 z-20 cursor-pointer hover:scale-110 active:scale-90 transition-transform duration-200"
              :style="{ left: t.x + 'px', top: t.y + 'px' }"
              title="點擊收拾垃圾"
            >
              <!-- Uncollected Crumpled Trash Paper SVG -->
              <svg class="w-full h-full fill-slate-400 stroke-slate-600 hover:fill-slate-500" viewBox="0 0 24 24" stroke-width="1.5">
                <path d="M12 2a10 10 0 1 0 10 10A10 10 0 0 0 12 2zm3.5 13.5l-1.5 1.5-3.5-3.5-3.5 3.5-1.5-1.5 3.5-3.5-3.5-3.5 1.5-1.5 3.5 3.5 3.5-3.5 1.5 1.5-3.5 3.5z" opacity="0.3"/>
                <path d="M8.5 14.5l-1-1.5 2-1 1 2zM15 11l-2-1-0.5 2 2.5 1zM11 15l2-0.5 0.5 2-1.5 0.5z" />
              </svg>
            </div>

            <!-- 6. Invisible Wiping Input Overlay (Topmost interaction catcher) -->
            <div 
              @mousedown="startCleaning"
              @mousemove="clean"
              @mouseup="stopCleaning"
              @mouseleave="stopCleaning"
              @touchstart="startCleaningTouch"
              @touchmove="cleanTouch"
              @touchend="stopCleaning"
              class="absolute inset-0 z-25 cleaning-canvas"
              :class="{ 'pointer-events-none': gameCompleted }"
            ></div>

            <!-- 7. Game Complete Knowledge Overlay Card -->
            <transition name="fade">
              <div 
                v-if="gameCompleted" 
                class="absolute inset-0 bg-navy/95 z-30 p-4 flex flex-col justify-between text-cream animate-fade-in"
              >
                <div class="space-y-1.5 flex-grow flex flex-col justify-center text-center">
                  <span class="text-[8px] tracking-[0.25em] text-oatmeal font-bold uppercase block">管家秩序思維</span>
                  <h4 class="text-xs font-serif leading-relaxed tracking-wider px-4">
                    "我們遵循「由上而下、先乾後濕」的管家法則：先收拾垃圾、擦拭櫃子檯面，再進行地面吸塵與濕拖拋光。這確保粉塵不交叉污染，還原居家空間的極致秩序。"
                  </h4>
                </div>
                
                <div class="pt-2 flex justify-center">
                  <router-link 
                    to="/contact"
                    class="btn-premium px-5 py-1.5 bg-oatmeal hover:bg-oatmeal-dark text-navy text-[9px] tracking-widest font-semibold rounded uppercase whitespace-nowrap"
                  >
                    立即預約管家服務
                  </router-link>
                </div>
              </div>
            </transition>
          </div>

          <!-- Vertical compact Toolbox -->
          <div class="w-[84px] shrink-0 flex flex-col justify-between border-l border-navy/5 pl-3 space-y-2">
            <span class="text-[8px] tracking-widest font-bold text-navy/40 uppercase block text-center">選擇工具</span>
            
            <div class="flex flex-col gap-2 flex-grow justify-center">
              <button 
                v-for="tool in tools" 
                :key="tool.id"
                @click="selectTool(tool.id)"
                class="flex flex-col items-center justify-center py-2 px-1 border rounded transition-all duration-300 relative"
                :class="[
                  selectedTool === tool.id 
                    ? 'bg-oatmeal border-navy text-navy font-semibold scale-102 shadow-sm' 
                    : 'bg-white border-navy/10 text-navy/60 hover:border-navy/20'
                ]"
              >
                <div class="w-6 h-6 flex items-center justify-center" v-html="tool.icon"></div>
                <span class="text-[8px] tracking-wider mt-0.5 block whitespace-nowrap">{{ tool.name }}</span>
              </button>
            </div>
          </div>
        </div>

        <!-- Copywriting below canvas -->
        <div class="text-center pt-2 border-t border-navy/5 flex flex-col items-center space-y-1">
          <p class="text-[11px] font-medium tracking-wider text-navy flex items-center justify-center space-x-2">
            <span>{{ instructionCopy }}</span>
          </p>
          <p class="text-[9px] text-navy/40 font-light flex items-center justify-center space-x-2">
            <span>{{ toolStatusHint }}</span>
            <button 
              v-if="!gameCompleted"
              @click="skipGame" 
              class="text-[9px] text-dust hover:text-navy underline cursor-pointer ml-1 font-semibold"
            >
              直接完成
            </button>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, computed, nextTick } from 'vue'

// Tools list
const tools = [
  { 
    id: 'CLOTH', 
    name: '纖維布', 
    desc: '吸水防靜電，適合清除櫃體髒污與檯面落塵。',
    icon: `<svg class="w-5 h-5 stroke-current fill-none" stroke-width="1.5" viewBox="0 0 24 24"><path d="M4 19V5a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2z"/><path d="M12 18H6"/><path d="M18 14H6"/><path d="M18 10H6"/><path d="M18 6H6"/></svg>` 
  },
  { 
    id: 'VACUUM', 
    name: '吸塵器', 
    desc: '強效吸除地面微塵與毛髮，防止揚塵二次污染。',
    icon: `<svg class="w-5 h-5 stroke-current fill-none" stroke-width="1.5" viewBox="0 0 24 24"><path d="M19 10H5a2 2 0 0 0-2 2v7a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7a2 2 0 0 0-2-2z"/><path d="M12 10V3M7 3h10"/></svg>` 
  },
  { 
    id: 'MOP', 
    name: '平拖把', 
    desc: '濕拖除垢、地板打磨拋光，不留水痕。',
    icon: `<svg class="w-5 h-5 stroke-current fill-none" stroke-width="1.5" viewBox="0 0 24 24"><path d="M5 20h14M12 20V4M3 20h18L12 4z"/></svg>` 
  }
]

// Interactive Game State
const selectedTool = ref('CLOTH')
const isDrawing = ref(false)

// 3 Crumpled Trash Items on Table (absolute coordinates on 400x300 canvas container)
const trashItems = ref([
  { x: 250, y: 145, collected: false },
  { x: 285, y: 150, collected: false },
  { x: 235, y: 155, collected: false }
])

// Individual Chore Completion States
const trashCleaned = ref(false)
const cabinetCleaned = ref(false)
const dustCleaned = ref(false)
const stainCleaned = ref(false)

// Canvas elements refs
const cabinetCanvasRef = ref(null)
const dustCanvasRef = ref(null)
const stainCanvasRef = ref(null)

let cabinetCtx = null
let dustCtx = null
let stainCtx = null

// Chores checklist
const chores = computed(() => [
  { id: 'trash', name: '收拾桌上垃圾 (直接點擊)', completed: trashCleaned.value },
  { id: 'cabinet', name: '擦拭櫃子髒污 (使用纖維布)', completed: cabinetCleaned.value },
  { id: 'dust', name: '地面吸塵除塵 (使用吸塵器)', completed: dustCleaned.value },
  { id: 'stain', name: '地面濕拖拋光 (使用平拖把)', completed: stainCleaned.value }
])

const completedCount = computed(() => {
  return chores.value.filter(c => c.completed).length
})

const gameCompleted = computed(() => {
  return completedCount.value === 4
})

const instructionCopy = computed(() => {
  if (gameCompleted.value) {
    return '客廳已恢復極致的秩序與純淨！'
  }
  if (!trashCleaned.value) {
    return '找碴提示：桌上有些散落的垃圾，請直接點擊拾取。'
  }
  if (selectedTool.value === 'CLOTH' && !cabinetCleaned.value) {
    return '工序：請拖曳纖維布在櫃子的汙垢處來回擦拭。'
  }
  if (selectedTool.value === 'VACUUM' && !dustCleaned.value) {
    return '工序：請拖曳吸塵器吸除地面上的灰色塵蟎。'
  }
  if (selectedTool.value === 'MOP' && !stainCleaned.value) {
    if (!dustCleaned.value) {
      return '管家守則：必須先完成「地面吸塵」，才能進行濕拖拋光！'
    }
    return '工序：請拖曳平拖把擦拭地面泥垢以打磨拋光。'
  }
  return '請在工具箱切換其他工具以處理剩餘的髒污項目。'
})

const toolStatusHint = computed(() => {
  if (gameCompleted.value) {
    return '卓越工藝，秩序重整完成。'
  }
  if (selectedTool.value === 'MOP' && !dustCleaned.value) {
    return '警告：直接拖地會讓灰塵化為泥水，請切換吸塵器先做除塵！'
  }
  return '切換右側工法工具，然後按住並在畫面髒污處擦拭。'
})

// Initialize dirt on separate canvas layers
const initCanvas = () => {
  // 1. Cabinet Canvas (Smudge marks)
  const cabCanvas = cabinetCanvasRef.value
  if (cabCanvas) {
    cabinetCtx = cabCanvas.getContext('2d')
    cabinetCtx.clearRect(0, 0, cabCanvas.width, cabCanvas.height)
    // Draw spots in cabinet area (x: 50~150, y: 130~230)
    cabinetCtx.fillStyle = 'rgba(110, 80, 50, 0.7)'
    cabinetCtx.beginPath()
    cabinetCtx.arc(75, 160, 10, 0, Math.PI * 2)
    cabinetCtx.fill()
    cabinetCtx.beginPath()
    cabinetCtx.arc(115, 175, 8, 0, Math.PI * 2)
    cabinetCtx.fill()
    cabinetCtx.beginPath()
    cabinetCtx.arc(95, 195, 12, 0, Math.PI * 2)
    cabinetCtx.fill()
  }

  // 2. Floor Dust Canvas (Dust Bunnies)
  const dustCanvas = dustCanvasRef.value
  if (dustCanvas) {
    dustCtx = dustCanvas.getContext('2d')
    dustCtx.clearRect(0, 0, dustCanvas.width, dustCanvas.height)
    // Draw dust balls in floor/rug area (x: 80~320, y: 200~280)
    dustCtx.fillStyle = 'rgba(100, 105, 115, 0.8)'
    dustCtx.beginPath()
    dustCtx.arc(130, 235, 10, 0, Math.PI * 2)
    dustCtx.fill()
    dustCtx.beginPath()
    dustCtx.arc(200, 255, 12, 0, Math.PI * 2)
    dustCtx.fill()
    dustCtx.beginPath()
    dustCtx.arc(280, 240, 8, 0, Math.PI * 2)
    dustCtx.fill()
    dustCtx.beginPath()
    dustCtx.arc(160, 260, 9, 0, Math.PI * 2)
    dustCtx.fill()
  }

  // 3. Floor Stain Canvas (Muddy footprints)
  const stainCanvas = stainCanvasRef.value
  if (stainCanvas) {
    stainCtx = stainCanvas.getContext('2d')
    stainCtx.clearRect(0, 0, stainCanvas.width, stainCanvas.height)
    // Draw mud spots (x: 80~320, y: 200~280)
    stainCtx.fillStyle = 'rgba(139, 94, 26, 0.65)'
    stainCtx.beginPath()
    stainCtx.arc(110, 255, 7, 0, Math.PI * 2)
    stainCtx.fill()
    stainCtx.beginPath()
    stainCtx.arc(245, 235, 9, 0, Math.PI * 2)
    stainCtx.fill()
    stainCtx.beginPath()
    stainCtx.arc(220, 265, 8, 0, Math.PI * 2)
    stainCtx.fill()
    stainCtx.beginPath()
    stainCtx.arc(310, 250, 10, 0, Math.PI * 2)
    stainCtx.fill()
  }
}

const selectTool = (toolId) => {
  selectedTool.value = toolId
}

// Click to collect trash on the table
const collectTrash = (idx) => {
  trashItems.value[idx].collected = true
  // Check if all trash items are collected
  if (trashItems.value.every(t => t.collected)) {
    trashCleaned.value = true
  }
}

// Skip game / Direct complete bypass
const skipGame = () => {
  trashItems.value.forEach(t => t.collected = true)
  trashCleaned.value = true
  cabinetCleaned.value = true
  dustCleaned.value = true
  stainCleaned.value = true
  
  // Clear all canvases
  if (cabinetCtx) cabinetCtx.clearRect(0, 0, 400, 300)
  if (dustCtx) dustCtx.clearRect(0, 0, 400, 300)
  if (stainCtx) stainCtx.clearRect(0, 0, 400, 300)
}

// Wiping interaction
const startCleaning = (e) => {
  if (gameCompleted.value) return
  isDrawing.value = true
  cleanAction(e.clientX, e.clientY)
}

const startCleaningTouch = (e) => {
  if (gameCompleted.value) return
  isDrawing.value = true
  if (e.touches && e.touches[0]) {
    cleanAction(e.touches[0].clientX, e.touches[0].clientY)
  }
}

const clean = (e) => {
  if (!isDrawing.value) return
  cleanAction(e.clientX, e.clientY)
}

const cleanTouch = (e) => {
  if (!isDrawing.value) return
  if (e.touches && e.touches[0]) {
    cleanAction(e.touches[0].clientX, e.touches[0].clientY)
  }
}

const stopCleaning = () => {
  isDrawing.value = false
  checkChoreCleanliness()
}

// Perform erase operation on active context
const cleanAction = (clientX, clientY) => {
  const activeCanvas = getActiveCanvas()
  const activeCtx = getActiveCtx()
  
  if (!activeCanvas || !activeCtx) return

  // Mop lock check (must vacuum dust first)
  if (selectedTool.value === 'MOP' && !dustCleaned.value) return

  const rect = activeCanvas.getBoundingClientRect()
  const x = (clientX - rect.left) * (activeCanvas.width / rect.width)
  const y = (clientY - rect.top) * (activeCanvas.height / rect.height)

  const brushRadius = 20

  activeCtx.globalCompositeOperation = 'destination-out'
  activeCtx.beginPath()
  activeCtx.arc(x, y, brushRadius, 0, Math.PI * 2)
  activeCtx.fill()

  throttleCheckChoreCleanliness()
}

const getActiveCanvas = () => {
  if (selectedTool.value === 'CLOTH') return cabinetCanvasRef.value
  if (selectedTool.value === 'VACUUM') return dustCanvasRef.value
  if (selectedTool.value === 'MOP') return stainCanvasRef.value
  return null
}

const getActiveCtx = () => {
  if (selectedTool.value === 'CLOTH') return cabinetCtx
  if (selectedTool.value === 'VACUUM') return dustCtx
  if (selectedTool.value === 'MOP') return stainCtx
  return null
}

let lastCheckTime = 0
const throttleCheckChoreCleanliness = () => {
  const now = Date.now()
  if (now - lastCheckTime > 120) {
    checkChoreCleanliness()
    lastCheckTime = now
  }
}

// Inspect active canvas pixel counts to check completeness
const checkChoreCleanliness = () => {
  const activeCanvas = getActiveCanvas()
  const activeCtx = getActiveCtx()
  
  if (!activeCanvas || !activeCtx) return

  const imgData = activeCtx.getImageData(0, 0, activeCanvas.width, activeCanvas.height)
  const pixels = imgData.data
  let remainingDirtyPixels = 0

  // Count how many pixels are still opaque (alpha > 10)
  for (let i = 3; i < pixels.length; i += 4) {
    if (pixels[i] > 10) remainingDirtyPixels++
  }

  // If remaining dirty pixels are below threshold, chore is complete
  if (remainingDirtyPixels < 60) {
    if (selectedTool.value === 'CLOTH') cabinetCleaned.value = true
    if (selectedTool.value === 'VACUUM') dustCleaned.value = true
    if (selectedTool.value === 'MOP') stainCleaned.value = true
    isDrawing.value = false
  }
}

onMounted(() => {
  initCanvas()
})
</script>

<style scoped>
@keyframes spin-slow {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
.animate-spin-slow {
  animation: spin-slow 20s linear infinite;
}

.sparkle-anim {
  animation: float 2s ease-in-out infinite;
}

@keyframes float {
  0%, 100% { transform: translateY(0px) scale(1); opacity: 0.8; }
  50% { transform: translateY(-5px) scale(1.1); opacity: 1; }
}

.animate-fade-in {
  animation: fadeIn 0.4s ease-out forwards;
}

.animate-slide-up {
  animation: slideUp 0.5s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideUp {
  from { transform: translateY(20px); opacity: 0; }
  to { transform: translateY(0); opacity: 1; }
}
</style>
