<script setup lang="ts">
import { Contact, UtensilsCrossed } from 'lucide-vue-next'

const props = defineProps<{
  icon: string
  title: string
  color: 'primary' | 'secondary' | 'tertiary'
}>()

const iconComponent = {
  Contact,
  UtensilsCrossed
}[props.icon]

const colorClasses = {
  primary: "bg-primary-container/20 text-primary-container",
  secondary: "bg-secondary-container/20 text-secondary",
  tertiary: "bg-tertiary-container/20 text-tertiary"
}
</script>

<template>
  <div class="glass p-4 rounded-xl flex items-center gap-4">
    <div :class="`w-10 h-10 shrink-0 rounded-lg flex items-center justify-center ${colorClasses[color]}`">
      <component :is="iconComponent" class="w-6 h-6" />
    </div>
    <h3 class="text-sm font-bold text-white">{{ title }}</h3>
  </div>
</template>
