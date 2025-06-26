<template>
  <footer 
    class="py-6 bg-indigo-950 text-white dark:bg-gray-900"
    v-motion
    :initial="{ opacity: 0 }"
    :visible-once="{ opacity: 1, transition: { delay: 200 } }"
  >
    <div class="">
      <p class="flex items-center justify-center gap-1">
        <span>Made with</span>
        <Icon 
          icon="mdi:heart" 
          class="text-red-500 animate-pulse" 
        />
        <span>by</span>
        <a 
          href="https://github.com/yourusername" 
          target="_blank"
          class="text-amber-300 hover:text-amber-400 transition-colors"
        >
          Mohamed Ayad
        </a>
      </p>
      
    </div>
  </footer>
</template>

<script setup>
import { Icon } from '@iconify/vue'
</script>