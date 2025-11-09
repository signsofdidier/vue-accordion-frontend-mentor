<script setup>
import FaqAccordion from "./components/FaqAccordion.vue";
</script>

<template>
  <main class="w-full h-full px-6">
    <!-- Background image top -->
    <header class="w-full h-[300px] absolute top-0 left-0">
      <img
        class="w-full h-full object-cover"
        src="@/assets/images/background-pattern-desktop.svg"
        alt="background pattern"
      />
    </header>

    <FaqAccordion class="relative shadow-lg my-20" />
  </main>
</template>

<style scoped></style>
