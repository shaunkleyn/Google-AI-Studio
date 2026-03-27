<script setup lang="ts">
import { Users } from 'lucide-vue-next'

defineProps<{
  icon: 'google' | 'linkedin'
  label: string
}>()
</script>

<template>
  <button class="flex items-center justify-center gap-3 bg-surface-container border border-outline-variant py-3 rounded-xl hover:bg-surface-container-highest transition-colors group">
    <template v-if="icon === 'google'">
      <img 
        alt="Google Logo" 
        class="w-5 h-5" 
        src="https://lh3.googleusercontent.com/aida-public/AB6AXuAK403srptNHfuEi4FJYftnCBoEktfXmemBdqh5yb7-IyCcfw5-WFLW4FWPNi2PEJ1E1oUluMmCIj3-pP1yuqMeUWUs2VLniqRs-bS3OWUFj2P4oL3thd1itgOAY8otV_9uQRkTuHxwzp8Td2ejOnzkWDne8y76nqaN-PQBgk8g8YEYhCpvsNsXZifSBxCkg8Uexqd4oObEE0adyDP41v4eo0uFBGqt1qKc4g6btWch-YTbPeiN5ARt9vi2tFlsJgKBdvG1oy1Xbv4"
        referrerPolicy="no-referrer"
      />
    </template>
    <template v-else>
      <Users class="w-5 h-5 text-secondary" />
    </template>
    <span class="text-sm font-bold text-on-surface">{{ label }}</span>
  </button>
</template>
