<script setup>
import { ref } from "vue";
import plusIcon from "@/assets/images/icon-plus.svg";
import minusIcon from "@/assets/images/icon-minus.svg";
import startIcon from "@/assets/images/icon-star.svg";

const faqs = ref([
  {
    id: 1,
    title: "What is Frontend Mentor, and how will it help me?",
    content: `Frontend Mentor offers realistic coding challenges to help developers improve their 
  frontend coding skills with projects in HTML, CSS, and JavaScript. It's suitable for 
  all levels and ideal for portfolio building.`,
    isOpen: true,
  },
  {
    id: 2,
    title: "Is Frontend Mentor free?",
    content: `Yes, Frontend Mentor offers both free and premium coding challenges, with the free 
  option providing access to a range of projects suitable for all skill levels.`,
    isOpen: false,
  },
  {
    id: 3,
    title: "Can I use Frontend Mentor projects in my portfolio?",
    content: `Yes, you can use projects completed on Frontend Mentor in your portfolio. It's an excellent
  way to showcase your skills to potential employers!`,
    isOpen: false,
  },
  {
    id: 4,
    title: "How can I get help if I'm stuck on a challenge?",
    content: `The best place to get help is inside Frontend Mentor's Discord community. There's a help 
  channel where you can ask questions and seek support from other community members.`,
    isOpen: false,
  },
]);

const isOpen = (clickedId) => {
  faqs.value.forEach((faq) => {
    faq.isOpen = faq.id === clickedId ? !faq.isOpen : false;
  });
};
</script>

<template>
  <section class="max-w-xl bg-white p-8 rounded-xl w-full mx-auto pt-10">
    <!-- title -->
    <div class="w-full flex items-center">
      <span><img :src="startIcon" alt="star icon" /></span>
      <h1 class="ms-4 text-6xl font-bold text-purple-950">FAQs</h1>
    </div>

    <!-- faq -->
    <section class="mt-8">
      <article
        v-for="faq in faqs"
        :key="faq.id"
        class="border-b border-gray-100 py-6 first:pt-0 last:pb-0 last:border-b-0"
      >
        <div
          @click="isOpen(faq.id)"
          class="flex justify-between items-center w-full cursor-pointer group"
        >
          <h2 class="text-lg font-semibold text-purple-950 group-hover:text-purple-500">
            {{ faq.title }}
          </h2>
          <span class="w-[50px] flex justify-end ms-5 md:ms-2"
            ><img :src="faq.isOpen ? minusIcon : plusIcon" alt="toggle icon"
          /></span>
        </div>
        <transition
          enter-active-class="transition-all duration-200 ease-in-out"
          enter-from-class="opacity-0 max-h-0 transform -translate-y-2"
          enter-to-class="opacity-100 max-h-96 transform translate-y-0"
          leave-active-class="transition-all duration-200 ease-in-out"
          leave-from-class="opacity-100 max-h-96 transform translate-y-0"
          leave-to-class="opacity-0 max-h-0 transform -translate-y-2"
        >
          <p v-if="faq.isOpen" class="text-sm text-purple-600 mt-5 overflow-hidden">
            {{ faq.content }}
          </p>
        </transition>
      </article>
    </section>
  </section>
</template>

<style scoped></style>
