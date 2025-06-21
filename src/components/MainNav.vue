<template>
  <nav
  ref="navbar"
  :class="[
      'flex justify-between p-4 fixed top-0 w-full z-50 transition-colors duration-300',
      !isHeroSectionVisible  ? 'bg-indigo-600' : ''
    ]"
    
  >
    <div class=" text-amber-300">Ayad</div>
    <ul
    :class="['flex  w-1/4 justify-between items-center text-white p-2 ',
      !isHeroSectionVisible  ? '' : 'shadow-md border border-indigo-600 bg-indigo-600/40 rounded-2xl backdrop-blur-sm'
    ]"
      
    >
      <li><a href="#RESUME" class=" text-amber-50  hover:text-amber-400" v-smooth-scroll="{duration:1500}">Resume</a></li>
      <li>Projects</li>
      <li>Contacts</li>
    </ul>
    <div>
      <ul class="flex justify-start">
        <li>
          <Icon icon="mdi:github" class="text-white" />
        </li>
        <li>
          <Icon icon="mdi:google" class="text-white" />
        </li>
        <li>
          <Icon icon="mdi:linkedin" class="text-white" />
        </li>
      </ul>
    </div>
  </nav>
</template>

<script setup>
import { Icon } from "@iconify/vue";
import { ref,onMounted,onUnmounted } from "vue";
const isHeroSectionVisible = ref(true)
let observer = null

onMounted(() => {
  setTimeout(() => {
    const heroSection = document.getElementById('heroSection')
    const otherSections = document.querySelectorAll('section[id]:not(#heroSection)')
    
    if (!heroSection) {
      console.error('Hero section not found!')
      return
    }

    observer = new IntersectionObserver(
      (entries) => {
        entries.forEach(entry => {
          if (entry.target.id === 'heroSection') {
            isHeroSectionVisible.value = entry.isIntersecting
          }
        })
      },
      {
        threshold: 0.1,
        rootMargin: '-100px 0px 0px 0px'
      }
    )

    observer.observe(heroSection)
    otherSections.forEach(section => observer.observe(section))
  }, 500)
})

onUnmounted(() => {
  if (observer) observer.disconnect()
})

</script>
