<template>
  <section id="contact" class="py-20 bg-gray-50 dark:bg-gray-900">
    <div class="container mx-auto px-4">
      <!-- العنوان مع تأثير حركي -->
      <h2 
        v-motion
        :initial="{ opacity: 0, y: 20 }"
        :visible-once="{ opacity: 1, y: 0 }"
        class="text-3xl font-bold text-center mb-16 text-indigo-600 dark:text-indigo-400"
      >
        تواصل معي
      </h2>

      <div class="grid md:grid-cols-2 gap-12 items-center">
        <!-- معلومات التواصل -->
        <div 
          v-motion
          :initial="{ opacity: 0, x: -30 }"
          :visible-once="{ opacity: 1, x: 0 }"
          class="space-y-8"
        >
          <!-- بطاقة معلومات -->
          <div 
            v-for="(contact, index) in contacts"
            :key="index"
            class="flex items-start gap-4 p-6 bg-white dark:bg-gray-800 rounded-xl shadow-md hover:shadow-lg transition-shadow"
          >
            <div class="p-3 bg-indigo-100 dark:bg-indigo-900 rounded-full">
              <Icon :icon="contact.icon" class="text-indigo-600 dark:text-indigo-300 text-xl" />
            </div>
            <div>
              <h3 class="text-lg font-semibold text-gray-800 dark:text-white">{{ contact.title }}</h3>
              <a 
                :href="contact.link" 
                target="_blank"
                class="text-gray-600 dark:text-gray-300 hover:text-indigo-500 dark:hover:text-indigo-400 transition-colors"
              >
                {{ contact.value }}
              </a>
            </div>
          </div>
        </div>

        <!-- نموذج التواصل -->
        <div 
          v-motion
          :initial="{ opacity: 0, x: 30 }"
          :visible-once="{ opacity: 1, x: 0 }"
          class="bg-white dark:bg-gray-800 p-8 rounded-xl shadow-md"
        >
          <h3 class="text-xl font-semibold mb-6 text-gray-800 dark:text-white">أرسل لي رسالة</h3>
          <form @submit.prevent="sendMessage" class="space-y-6">
            <div>
              <label for="name" class="block mb-2 text-gray-700 dark:text-gray-300">الاسم</label>
              <input
                v-model="form.name"
                type="text"
                id="name"
                required
                class="w-full px-4 py-2 border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 dark:bg-gray-700"
              >
            </div>
            
            <div>
              <label for="email" class="block mb-2 text-gray-700 dark:text-gray-300">البريد الإلكتروني</label>
              <input
                v-model="form.email"
                type="email"
                id="email"
                required
                class="w-full px-4 py-2 border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 dark:bg-gray-700"
              >
            </div>
            
            <div>
              <label for="message" class="block mb-2 text-gray-700 dark:text-gray-300">الرسالة</label>
              <textarea
                v-model="form.message"
                id="message"
                rows="4"
                required
                class="w-full px-4 py-2 border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 dark:bg-gray-700"
              ></textarea>
            </div>
            
            <button
              type="submit"
              class="w-full bg-indigo-600 hover:bg-indigo-700 text-white py-3 px-6 rounded-lg transition-colors"
            >
              إرسال الرسالة
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Icon } from '@iconify/vue'
import { ref } from 'vue'

// بيانات التواصل
const contacts = [
  {
    title: "البريد الإلكتروني",
    value: "example@email.com",
    icon: "mdi:email-outline",
    link: "mailto:example@email.com"
  },
  {
    title: "الهاتف",
    value: "+20 123 456 789",
    icon: "mdi:phone-outline",
    link: "tel:+20123456789"
  },
  {
    title: "GitHub",
    value: "github.com/yourusername",
    icon: "mdi:github",
    link: "https://github.com/yourusername"
  },
  {
    title: "LinkedIn",
    value: "linkedin.com/in/yourprofile",
    icon: "mdi:linkedin",
    link: "https://linkedin.com/in/yourprofile"
  }
]

// نموذج الرسالة
const form = ref({
  name: '',
  email: '',
  message: ''
})

// إرسال الرسالة
const sendMessage = () => {
  // هنا يمكنك إضافة منطق إرسال الرسالة (مثل API call)
  console.log('تم إرسال الرسالة:', form.value)
  
  // إعادة تعيين النموذج بعد الإرسال
  form.value = {
    name: '',
    email: '',
    message: ''
  }
  
  alert('تم إرسال رسالتك بنجاح! سأتواصل معك قريبًا.')
}
</script>

<style scoped>
/* تأثيرات إضافية */
textarea {
  min-height: 120px;
  resize: vertical;
}
</style>