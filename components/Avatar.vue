<script setup lang="ts">
defineProps<{
  src: string
}>()
</script>

<template>
  <div class="w-8 h-8 rounded-full border-2 border-[#080E1C] overflow-hidden">
    <img 
      class="w-full h-full object-cover" 
      :src="src" 
      alt="User"
      referrerPolicy="no-referrer"
    />
  </div>
</template>
