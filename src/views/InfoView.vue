<template>
  <div class="max-w-4xl mx-auto py-4 space-y-12">
    <!-- Header -->
    <div class="text-center space-y-2">
      <span class="text-xs tracking-[0.25em] text-dust font-bold uppercase block">Service Standards</span>
      <h2 class="text-3xl font-serif text-navy font-semibold">服務指南與標準</h2>
      <p class="text-xs text-navy/50 tracking-wider">傳承極致管家精神，為您的起居空間制定秩序規範</p>
    </div>

    <!-- Section 1: Workflow Steps -->
    <div class="space-y-6">
      <h3 class="font-serif text-xl text-navy font-semibold text-center md:text-left">管家級服務流程</h3>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
        <div 
          v-for="(step, idx) in steps" 
          :key="idx"
          class="bg-white border border-navy/10 rounded-lg p-5 flex flex-col justify-between shadow-sm hover:border-navy/30 transition-all duration-300 relative group"
        >
          <span class="absolute top-4 right-4 text-3xl font-serif font-bold text-oatmeal group-hover:text-navy/10 transition-colors duration-300">
            0{{ idx + 1 }}
          </span>
          <div class="space-y-3 pt-4">
            <h4 class="text-sm font-semibold tracking-wider text-navy">{{ step.title }}</h4>
            <p class="text-xs text-navy/60 leading-relaxed font-light">{{ step.desc }}</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Section 2: Pricing Table -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-start">
      <!-- Rates Table -->
      <div class="space-y-4 bg-white border border-navy/10 rounded-lg p-6 shadow-sm">
        <h3 class="font-serif text-lg text-navy font-semibold">標準收費參考</h3>
        <p class="text-xs text-navy/50 leading-relaxed font-light">
          我們堅持價格透明，無額外隱藏費用。所有預約皆包含標準清潔耗材。
        </p>

        <div class="overflow-x-auto pt-2">
          <table class="w-full text-left text-xs tracking-wider border-collapse">
            <thead>
              <tr class="border-b border-navy/10 text-[10px] text-navy/40 font-bold uppercase">
                <th class="py-2.5">服務項目</th>
                <th class="py-2.5">計費標準</th>
                <th class="py-2.5 text-right">費用 (TWD)</th>
              </tr>
            </thead>
            <tbody class="divide-y divide-navy/5 text-navy/80 font-light">
              <tr v-for="rate in rates" :key="rate.name">
                <td class="py-3 font-medium text-navy">{{ rate.name }}</td>
                <td class="py-3">{{ rate.unit }}</td>
                <td class="py-3 text-right font-semibold text-navy">{{ rate.price }}</td>
              </tr>
            </tbody>
          </table>
        </div>
        <p class="text-[9px] text-navy/40 font-light leading-normal pt-2">
          * 註：深度清潔及大理石防護拋光等特種項目，將依現場髒污程度及坪數另行評估。
        </p>
      </div>

      <!-- Trust Badges & Policies -->
      <div class="space-y-6 flex flex-col justify-between h-full">
        <div class="bg-navy text-cream p-6 rounded-lg border border-navy-light shadow-sm space-y-4">
          <h3 class="font-serif text-lg text-oatmeal font-semibold">卓越承諾</h3>
          <div class="space-y-4 pt-2">
            <div 
              v-for="policy in policies" 
              :key="policy.title"
              class="flex items-start space-x-3"
            >
              <div class="w-5 h-5 rounded-full bg-cream/10 flex items-center justify-center text-oatmeal shrink-0 mt-0.5">
                ✓
              </div>
              <div class="space-y-0.5 text-left">
                <h4 class="text-xs font-semibold tracking-wider text-oatmeal">{{ policy.title }}</h4>
                <p class="text-[11px] text-cream/70 leading-relaxed font-light">{{ policy.desc }}</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Call to action card -->
        <div class="bg-oatmeal/40 border border-navy/10 rounded-lg p-6 flex flex-col items-center justify-center text-center space-y-4">
          <h4 class="font-serif text-sm font-semibold text-navy">尋求專屬空間的秩序重整？</h4>
          <p class="text-xs text-navy/60 font-light max-w-xs leading-relaxed">
            與專業管家顧問進行線上對談，我們將為您規劃專屬的空間重整方案。
          </p>
          <router-link 
            to="/contact" 
            class="btn-premium px-6 py-2.5 bg-navy text-cream text-[10px] tracking-widest uppercase font-bold rounded"
          >
            立即線上預約
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const steps = [
  { 
    title: '預約與諮詢', 
    desc: '線上填寫表單或致電，管家顧問在一小時內與您取得聯繫，確認基本環境資訊。' 
  },
  { 
    title: '現場評估規劃', 
    desc: '專業管家親臨現場（或視訊進行），量測建材材質並規劃專屬去污工序。' 
  },
  { 
    title: '職人精準清潔', 
    desc: '攜帶環保中性清潔劑與專業工法耗材，依工序有條不紊地進行秩序除污維護。' 
  },
  { 
    title: '管家級複檢確認', 
    desc: '清潔完畢後進行大理石光澤度、鏡面水痕等 36 項指標複檢，雙方滿意後才行結案。' 
  }
]

const rates = [
  { name: '日常管家清潔', unit: '4 小時 / 單次', price: '$2,400 起' },
  { name: '深度大掃除', unit: '8 小時 / 雙人組', price: '$8,800 起' },
  { name: '廚房重油污處理', unit: '灶台、抽油煙機', price: '$3,200 起' },
  { name: '浴室水垢石灰整治', unit: '玻璃乾濕分離、洗手槽', price: '$2,800 起' },
  { name: '裝潢細清拋光', unit: '每坪計費', price: '$600 - $1,200' }
]

const policies = [
  { 
    title: '100% 滿意承諾', 
    desc: '結案後 24 小時內若有任何不滿意，我們將免費指派管家前往進行二次加強清潔。' 
  },
  { 
    title: '環保與建材守護', 
    desc: '堅持使用無毒、生物降解中性洗劑。針對大理石、實木等天然石材與木器，均搭配防護工法，保證絕不刮傷。' 
  },
  { 
    title: '管家誠信擔保', 
    desc: '所有清潔專員皆經過背景調查並備有良民證，且服務過程全程投保責任險。' 
  }
]
</script>
