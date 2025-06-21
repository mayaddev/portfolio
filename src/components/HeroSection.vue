
<template>
  <section
  id="heroSection"
    class="min-h-screen flex items-center justify-center bg-center bg-no-repeat bg-cover text-white"
    :style="{ backgroundImage: `url(${bgImage})` }"
  >
    <div class="grid lg:grid-cols-2 md:grid-cols-1 bg-indigo-600 w-3/4">
      <div class="justify-center items-center p-4">
        <h1
          class="text-4xl sm:text-5xl md:text-6xl font-bold mb-4"
          v-motion-pop-visible-once
        >
          Hello, I am <span class="text-yellow-400">Mohamed Ayad</span>
        </h1>
        <h2
          class="text-xl sm:text-2xl md:text-3xl font-medium mb-4"
          v-motion-pop-visible-once
        >
          Frontend Developer & Data Analyst
        </h2>
        <p
          class="text-base sm:text-lg text-gray-300 max-w-xl mx-auto"
          v-motion-pop-visible-once
        >
          I build modern web interfaces using Vue.js & Nuxt, and I transform
          data into powerful insights using Python and visualization tools.
        </p>
      </div>
      <div class="flex justify-end">
        <img
          v-motion
          :initial="initial"
          :enter="enter"
          src="../assets/me.png"
          alt="Mohamed Ayad"
          class="w-full h-auto max-w-md rounded-xl"
        />
      </div>
    </div>
  </section>
</template>
<script setup>
import bgImage from "@/assets/bg.svg";
import { ref } from "vue";
const initial = ref({
  opacity: 0,
});

const enter = ref({
  opacity: 1,
  transition: {
    delay: 300,
  },
});

const visible = ref({});
</script>
