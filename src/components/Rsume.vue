<template>
  <section 
  id="RESUME"
    ref="section"
    class="min-h-screen flex items-center justify-center bg-indigo-950 py-12"
  >
    <div class="container mx-auto px-4">
      <!-- Card رئيسي مع تأثيرات متتالية -->
      <div
        v-motion
        :initial="{
          opacity: 0,
          y: 50,
          scale: 0.98
        }"
        :visible-once="{
          opacity: 1,
          y: 0,
          scale: 1,
          transition: {
            type: 'spring',
            stiffness: 150,
            damping: 15,
            mass: 0.5,
            delay: 200
          }
        }"
        class="bg-white rounded-xl shadow-2xl overflow-hidden max-w-4xl w-full"
      >
        <div class="p-8 md:p-12">
          <!-- العنوان الرئيسي -->
          <h1
            v-motion
            :initial="{ opacity: 0, x: -30 }"
            :visible-once="{
              opacity: 1,
              x: 0,
              transition: {
                delay: 300,
                type: 'spring',
                stiffness: 200
              }
            }"
            class="text-3xl font-bold text-gray-800 mb-8"
          >
            My Resume
          </h1>

          <!-- محتوى السيرة الذاتية -->
          <div class="space-y-8">
            <!-- كل قسم مع تأثير متتالي -->
            <div
              v-for="(section, index) in resumeSections"
              :key="section.title"
              v-motion
              :initial="{ opacity: 0, y: 20 }"
              :visible-once="{
                opacity: 1,
                y: 0,
                transition: {
                  delay: 400 + index * 100,
                  type: 'spring',
                  stiffness: 150
                }
              }"
              class="group"
            >
              <div class="flex items-start gap-4">
                <!-- أيقونة -->
                <div
                  v-motion
                  :initial="{ scale: 0 }"
                  :visible-once="{
                    scale: 1,
                    transition: {
                      delay: 400 + index * 100,
                      type: 'spring'
                    }
                  }"
                  class="p-2 bg-indigo-100 rounded-full mt-1"
                >
                  <Icon 
                    :icon="section.icon" 
                    class="text-indigo-600 text-xl" 
                  />
                </div>
                
                <!-- المحتوى -->
                <div>
                  <h2 class="text-xl font-semibold text-indigo-600 mb-1">
                    {{ section.title }}
                  </h2>
                  <p class="text-gray-600">{{ section.content }}</p>
                  
                  <!-- تفاصيل إضافية -->
                  <div 
                    v-if="section.details"
                    class="mt-2 pl-4 border-l-2 border-indigo-200"
                  >
                    <p 
                      v-for="(detail, i) in section.details"
                      :key="i"
                      class="text-gray-500 text-sm"
                    >
                      • {{ detail }}
                    </p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Icon } from '@iconify/vue'

const resumeSections = [
  {
    title: "Experience",
    icon: "mdi:briefcase",
    content: "5+ years as UI/UX Designer and Data Analyst",
    details: [
      "Senior UI Designer at XYZ (2020-Present)",
      "Data Analyst at ABC (2018-2020)"
    ]
  },
  {
    title: "Education",
    icon: "mdi:school",
    content: "Bachelor's in Computer Science",
    details: [
      "Cairo University (2014-2018)",
      "GPA: 3.8/4.0"
    ]
  },
  {
    title: "Skills",
    icon: "mdi:tools",
    content: "Technical Expertise",
    details: [
      "Frontend: Vue.js, TailwindCSS",
      "Data Analysis: Python, Pandas",
      "Design: Figma, Adobe XD"
    ]
  }
]
</script>