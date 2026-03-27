<script setup lang="ts">
import { ShieldCheck, Contact, UtensilsCrossed } from 'lucide-vue-next'
import { motion } from 'motion/vue'

defineProps<{
  badge: string
  title: string
  description: string
  buttonText: string
}>()

defineEmits(['toggle'])
</script>

<template>
  <div class="relative z-10 max-w-2xl">
    <!-- Watermark Icon -->
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 opacity-5 pointer-events-none scale-150">
      <ShieldCheck class="w-[40rem] h-[40rem] stroke-[0.5]" />
    </div>

    <motion.header 
      :initial="{ opacity: 0, y: 20 }"
      :animate="{ opacity: 1, y: 0 }"
      :transition="{ duration: 0.6, delay: 0.2 }"
      class="mb-12"
    >
      <span class="inline-block px-4 py-1.5 rounded-full bg-secondary-container/30 text-secondary text-xs font-bold tracking-widest uppercase mb-6 border border-secondary/20">
        {{ badge }}
      </span>
      <h2 class="text-5xl lg:text-6xl font-extrabold text-white leading-[1.1] tracking-tight mb-8">
        Powering the future of <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary">digital identity.</span>
      </h2>
      <p class="text-on-surface-variant text-lg mb-8 max-w-md">{{ description }}</p>
      <motion.button
        :while-hover="{ scale: 1.05 }"
        :while-tap="{ scale: 0.95 }"
        @click="$emit('toggle')"
        class="px-8 py-3 rounded-xl border-2 border-primary text-primary font-bold hover:bg-primary hover:text-on-primary transition-all"
      >
        {{ buttonText }}
      </motion.button>
    </motion.header>

    <div class="grid grid-cols-1 gap-4 opacity-60">
      <FeatureCardSmall 
        icon="Contact"
        title="Digital Business Cards"
        color="primary"
      />
      <FeatureCardSmall 
        icon="UtensilsCrossed"
        title="Smart Menus"
        color="secondary"
      />
    </div>

    <div class="mt-12 flex items-center gap-6">
      <div class="flex -space-x-3">
        <Avatar src="https://lh3.googleusercontent.com/aida-public/AB6AXuAO3vxQIvD7PFKb-3gxBc_giR2Kj_lO63Fw-7b95nPUMWcwXuhjws_t579F2GEsSHcuDNqUTy9T-TxizQx-znnRhsdnH7rVIdL_mWUfJhVZEaWiFyWLgkQlvOktd0lqyEIspSGMdSUiQ_F7GpxPugdkqBl54Umvy9dxAf92o0b-KP0wr-6RqlM5n8exv6Dsn7M7AoItKyf6R_5MH0HxD597NKPViLYEkYDAU9gKK86rNsW6Mxuaq1pDBdIyMA8XCGepsqS_GvFohZ4" />
        <Avatar src="https://lh3.googleusercontent.com/aida-public/AB6AXuBNM4W_0TAOkbsIYbV9xaiyQ2Diy10vcjsquKBD5gtAwOYriGFo8zw-4g9RVO5bgya_OK4tCXVevPO8tdk9UZ-T3-jMRtVnNVqwV_fJJYBXfR58Avw78SIVnPFIrwP-FSIOhrLfcTVZ8GdqKyPqMYl_dXAWkGabQ5_TQphLf4zD88uoh0CjtgH_jZQxFlaLmy86XlHZJGuvKvSo-kbvzlcmsPFWVhhQoBZZjFzWVbFQxhhSdnl45N-SCChHFq77pdAA24sqBlKyHXA" />
        <div class="w-8 h-8 rounded-full border-2 border-[#080E1C] bg-surface-container-high flex items-center justify-center text-[8px] font-bold text-primary">
          +2k
        </div>
      </div>
      <p class="text-[10px] text-on-surface-variant max-w-[150px] leading-snug">
        Joined by <span class="text-white font-bold">2,000+ businesses</span>.
      </p>
    </div>
  </div>
</template>
