<template>
  <div class="max-w-4xl mx-auto py-4 space-y-8 relative">
    
    <!-- Header -->
    <div class="text-center space-y-2">
      <span class="text-xs tracking-[0.25em] text-dust font-bold uppercase block">Book An Appointment</span>
      <h2 class="text-3xl font-serif text-navy font-semibold">與我們聯繫</h2>
      <p class="text-xs text-navy/50 tracking-wider">與我們攜手，為您的起居空間注入秩序與純淨</p>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-stretch mt-8 relative">
      <!-- Left Column: Contact info and hours -->
      <div class="flex flex-col justify-between p-6 bg-white border border-navy/10 rounded-lg shadow-sm space-y-8 relative overflow-hidden group">
        <!-- Floating Dust Sprite Easter Egg (peeking from side) -->
        <div class="absolute -bottom-4 -left-4 opacity-25 group-hover:opacity-40 transition-opacity duration-300 pointer-events-none select-none">
          <svg class="w-16 h-16 fill-navy" viewBox="0 0 100 100">
            <path d="M 50 15 L 53 30 L 68 20 L 61 35 L 80 30 L 68 45 L 85 50 L 68 55 L 80 70 L 61 65 L 68 80 L 53 70 L 50 85 L 47 70 L 32 80 L 39 65 L 20 70 L 32 55 L 15 50 L 32 45 L 20 30 L 39 35 L 32 20 L 47 30 Z" />
            <circle cx="38" cy="48" r="10" fill="white" />
            <circle cx="38" cy="48" r="4.5" fill="black" />
            <circle cx="62" cy="48" r="10" fill="white" />
            <circle cx="62" cy="48" r="4.5" fill="black" />
          </svg>
        </div>

        <div class="space-y-6">
          <h3 class="font-serif text-lg text-navy font-semibold">快速聯繫管道</h3>
          <p class="text-xs text-navy/60 leading-relaxed font-light">
            不論是定期維護、深度大掃除或是商務空間整理，我們的專業管家顧問皆能提供專屬客製化方案。歡迎直接來電或來信。
          </p>

          <div class="space-y-4 pt-2">
            <!-- Phone -->
            <a href="tel:+886212345678" class="flex items-center space-x-4 p-3 rounded border border-transparent hover:border-navy/10 hover:bg-cream/40 transition-all duration-300 group/item">
              <div class="w-8 h-8 rounded-full bg-oatmeal flex items-center justify-center text-navy shrink-0 group-hover/item:bg-navy group-hover/item:text-cream transition-colors duration-300">
                <svg class="w-4 h-4 stroke-current fill-none" stroke-width="2" viewBox="0 0 24 24"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/></svg>
              </div>
              <div class="text-left">
                <span class="text-[10px] tracking-widest text-navy/40 font-bold block uppercase">PHONE</span>
                <span class="text-sm font-semibold tracking-wider text-navy">(+886) 2-1234-5678</span>
              </div>
            </a>

            <!-- Email -->
            <a href="mailto:service@masterhouse.tw" class="flex items-center space-x-4 p-3 rounded border border-transparent hover:border-navy/10 hover:bg-cream/40 transition-all duration-300 group/item">
              <div class="w-8 h-8 rounded-full bg-oatmeal flex items-center justify-center text-navy shrink-0 group-hover/item:bg-navy group-hover/item:text-cream transition-colors duration-300">
                <svg class="w-4 h-4 stroke-current fill-none" stroke-width="2" viewBox="0 0 24 24"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
              </div>
              <div class="text-left">
                <span class="text-[10px] tracking-widest text-navy/40 font-bold block uppercase">EMAIL</span>
                <span class="text-sm font-semibold tracking-wider text-navy">service@masterhouse.tw</span>
              </div>
            </a>
          </div>
        </div>

        <!-- Working hours -->
        <div class="pt-6 border-t border-navy/5 text-left space-y-1">
          <span class="text-[9px] tracking-widest text-navy/40 font-bold uppercase block">SERVICE HOURS</span>
          <p class="text-xs text-navy/60 leading-relaxed font-light">
            週一至週日 08:30 – 20:30 (除夕至初二休)<br />
            諮詢回覆時效：一小時內確認回電。
          </p>
        </div>
      </div>

      <!-- Right Column: Lead Capture Form (Dark Deep Navy Theme) -->
      <div class="bg-navy text-cream p-8 rounded-lg shadow-lg relative overflow-hidden flex flex-col justify-between border border-navy-light">
        
        <!-- Subtle Dust Sprite Easter Egg top-right -->
        <div class="absolute -top-3 -right-3 opacity-20 hover:opacity-45 transition-opacity duration-300 pointer-events-none select-none">
          <svg class="w-12 h-12 fill-cream" viewBox="0 0 100 100">
            <path d="M 50 15 L 53 30 L 68 20 L 61 35 L 80 30 L 68 45 L 85 50 L 68 55 L 80 70 L 61 65 L 68 80 L 53 70 L 50 85 L 47 70 L 32 80 L 39 65 L 20 70 L 32 55 L 15 50 L 32 45 L 20 30 L 39 35 L 32 20 L 47 30 Z" />
            <circle cx="38" cy="48" r="10" fill="navy" />
            <circle cx="38" cy="48" r="4.5" fill="white" />
            <circle cx="62" cy="48" r="10" fill="navy" />
            <circle cx="62" cy="48" r="4.5" fill="white" />
          </svg>
        </div>

        <form v-if="!formSubmitted" @submit.prevent="submitForm" class="space-y-5">
          <div class="space-y-1">
            <h3 class="font-serif text-lg font-semibold text-oatmeal">尊榮服務諮詢</h3>
            <p class="text-[10px] text-cream/40 tracking-wider">填寫下列表單，我們將由專人與您聯繫</p>
          </div>

          <!-- Name field -->
          <div class="space-y-1 text-left">
            <label for="name" class="text-[10px] tracking-widest text-oatmeal font-bold uppercase">姓名 / NAME</label>
            <input 
              type="text" 
              id="name"
              v-model="formData.name"
              required
              class="w-full bg-navy-dark border border-cream/10 rounded px-4 py-2.5 text-xs text-cream focus:outline-none focus:border-oatmeal focus:ring-1 focus:ring-oatmeal transition-all placeholder-cream/20"
              placeholder="您的稱呼"
            />
          </div>

          <!-- Email field -->
          <div class="space-y-1 text-left">
            <label for="email" class="text-[10px] tracking-widest text-oatmeal font-bold uppercase">電子信箱 / EMAIL</label>
            <input 
              type="email" 
              id="email"
              v-model="formData.email"
              required
              class="w-full bg-navy-dark border border-cream/10 rounded px-4 py-2.5 text-xs text-cream focus:outline-none focus:border-oatmeal focus:ring-1 focus:ring-oatmeal transition-all placeholder-cream/20"
              placeholder="example@email.com"
            />
          </div>

          <!-- Message field -->
          <div class="space-y-1 text-left">
            <label for="message" class="text-[10px] tracking-widest text-oatmeal font-bold uppercase">需求細節 / MESSAGE</label>
            <textarea 
              id="message"
              v-model="formData.message"
              required
              rows="4"
              class="w-full bg-navy-dark border border-cream/10 rounded px-4 py-2.5 text-xs text-cream focus:outline-none focus:border-oatmeal focus:ring-1 focus:ring-oatmeal transition-all placeholder-cream/20 resize-none"
              placeholder="請填寫您的清潔項目與期望預約時間（例：大理石洗手槽除垢、瓦斯爐台重油垢去油）"
            ></textarea>
          </div>

          <!-- Submit Button -->
          <button 
            type="submit"
            :disabled="isSubmitting"
            class="btn-premium w-full py-3 bg-oatmeal text-navy font-bold text-xs tracking-widest uppercase rounded hover:bg-oatmeal-dark transition-all duration-300 flex items-center justify-center space-x-2"
          >
            <span v-if="isSubmitting" class="w-3.5 h-3.5 border-2 border-navy border-t-transparent rounded-full animate-spin"></span>
            <span>{{ isSubmitting ? 'SUBMITTING...' : 'SUBMIT' }}</span>
          </button>
        </form>

        <!-- Success view -->
        <div v-else class="py-12 px-4 text-center space-y-6 flex flex-col items-center justify-center h-full animate-fade-in">
          <div class="w-16 h-16 rounded-full bg-oatmeal/10 flex items-center justify-center text-oatmeal border border-oatmeal/20">
            <svg class="w-8 h-8 stroke-current fill-none" stroke-width="2" viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg>
          </div>
          <div class="space-y-2">
            <h3 class="font-serif text-xl text-oatmeal font-semibold">預約訊息已送出</h3>
            <p class="text-xs text-cream/70 leading-relaxed font-light max-w-sm">
              感謝您的信任。我們已接收到您的需求，專屬管家顧問將於 2 小時內為您確認詳細排程並回電。
            </p>
          </div>
          <button 
            @click="resetForm"
            class="btn-premium px-6 py-2.5 bg-cream/10 hover:bg-cream/20 text-cream border border-cream/20 text-xs tracking-widest font-semibold rounded uppercase transition-all duration-300"
          >
            重新填寫
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const formData = reactive({
  name: '',
  email: '',
  message: ''
})

const isSubmitting = ref(false)
const formSubmitted = ref(false)

const submitForm = () => {
  isSubmitting.value = true
  
  // Simulate API submission
  setTimeout(() => {
    isSubmitting.value = false
    formSubmitted.value = true
  }, 1000)
}

const resetForm = () => {
  formData.name = ''
  formData.email = ''
  formData.message = ''
  formSubmitted.value = false
}
</script>

<style scoped>
.animate-fade-in {
  animation: fadeIn 0.4s ease-out forwards;
}

@keyframes fadeIn {
  from { opacity: 0; transform: scale(0.98); }
  to { opacity: 1; transform: scale(1); }
}
</style>
