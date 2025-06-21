<template>
  <section id="projects" class="py-20 bg-indigo-950">
    <div class="container mx-auto px-4">
      <!-- العنوان مع تأثير حركي -->
      <h2 
        v-motion
        :initial="{ opacity: 0, y: 20 }"
        :visible-once="{ opacity: 1, y: 0 }"
        class="text-3xl font-bold text-center mb-16 text-indigo-600 dark:text-indigo-400"
      >
        Projects
      </h2>

      <!-- شبكة المشاريع -->
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <!-- كل بطاقة مشروع -->
        <div
          v-for="(project, index) in projects"
          :key="project.id"
          v-motion
          :initial="{ opacity: 0, y: 30 }"
          :visible-once="{
            opacity: 1,
            y: 0,
            transition: {
              delay: 100 * index,
              type: 'spring',
              stiffness: 150
            }
          }"
          class="bg-white dark:bg-gray-800 rounded-xl shadow-lg overflow-hidden hover:shadow-xl transition-shadow duration-300"
        >
          <!-- صورة المشروع -->
          <div class="h-48 overflow-hidden">
            <img
              :src="`${project.image}`"
              :alt="project.title"
              class="w-full h-full object-cover hover:scale-105 transition-transform duration-500"
            />
          </div>

          <!-- محتوى البطاقة -->
          <div class="p-6">
            <h3 class="text-xl font-semibold text-gray-800 dark:text-white mb-2">
              {{ project.title }}
            </h3>
            <p class="text-gray-600 dark:text-gray-300 mb-4">
              {{ project.description }}
            </p>

            <!-- تقنيات المستخدمة -->
            <div class="flex flex-wrap gap-2 mb-4">
              <span
                v-for="tech in project.technologies"
                :key="tech"
                class="px-3 py-1 bg-indigo-100 dark:bg-indigo-900 text-indigo-800 dark:text-indigo-200 rounded-full text-sm"
              >
                {{ tech }}
              </span>
            </div>

            <!-- روابط المشروع -->
            <div class="flex space-x-3">
              <a
                :href="project.liveUrl"
                target="_blank"
                class="flex items-center text-indigo-600 dark:text-indigo-400 hover:text-indigo-800 dark:hover:text-indigo-300"
              >
                <Icon icon="mdi:web" class="mr-1" /> Live
              </a>
              <a
                :href="project.codeUrl"
                target="_blank"
                class="flex items-center text-gray-600 dark:text-gray-400 hover:text-gray-800 dark:hover:text-gray-300"
              >
                <Icon icon="mdi:github" class="mr-1" /> Code
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Icon } from '@iconify/vue'
import Project1Img from '@/assets/project-1.png'
// import Project2Img from '@/assets/images/project2.jpg'
// import Project3Img from '@/assets/images/project3.jpg'

const projects = [
  {
    id: 1,
    title: "نظام تحليل البيانات",
    description: "منصة لتحليل وعرض البيانات باستخدام Vue.js و Python",
    image: Project1Img,
    technologies: ["Vue.js", "TailwindCSS", "Python", "Chart.js"],
    liveUrl: "#",
    codeUrl: "#"
  },
  {
    id: 2,
    title: "متجر إلكتروني",
    description: "متجر متكامل مع نظام دفع وإدارة منتجات",
    image: Project1Img,
    technologies: ["Vue.js", "Pinia", "Node.js", "MongoDB"],
    liveUrl: "#",
    codeUrl: "#"
  },
  {
    id: 3,
    title: "لوحة تحكم إدارية",
    description: "لوحة تحكم لإدارة المستخدمين والمحتوى",
    image: Project1Img,
    technologies: ["React", "TailwindCSS", "Firebase"],
    liveUrl: "#",
    codeUrl: "#"
  },
    {
    id: 3,
    title: "لوحة تحكم إدارية",
    description: "لوحة تحكم لإدارة المستخدمين والمحتوى",
    image: Project1Img,
    technologies: ["React", "TailwindCSS", "Firebase"],
    liveUrl: "#",
    codeUrl: "#"
  },
    {
    id: 3,
    title: "لوحة تحكم إدارية",
    description: "لوحة تحكم لإدارة المستخدمين والمحتوى",
    image: Project1Img,
    technologies: ["React", "TailwindCSS", "Firebase"],
    liveUrl: "#",
    codeUrl: "#"
  }
]
</script>