<script setup>
import { Award, Lightbulb, Users, Scale, Leaf } from "lucide-vue-next";

const values = [
  { id: 1, icon: Award, text: "Excellence", color: "bg-blue-50" },
  { id: 2, icon: Lightbulb, text: "Innovation", color: "bg-teal-50" },
  { id: 3, icon: Users, text: "Collaboration", color: "bg-cyan-50" },
  { id: 4, icon: Scale, text: "integrity,", color: "bg-emerald-50" },
  { id: 5, icon: Leaf, text: "sustainability", color: "bg-teal-50" },
];
</script>

<template>
  <section
    class="relative w-full min-h-screen py-16 md:py-24 bg-gradient-to-b from-sky-10 via-blue-50/30 to-white text-center overflow-hidden"
  >
    <div
      class="absolute inset-0 opacity-30 pointer-events-none"
      style="
        background-image: radial-gradient(circle, #cbd5e1 1px, transparent 1px);
        background-size: 24px 24px;
        background-position: center center;
      "
    ></div>

    <!-- Blue gradient overlay -->
    <div
      class="absolute top-0 left-1/2 -translate-x-1/2 w-full h-full opacity-20 pointer-events-none"
    >
      <div
        class="absolute inset-0 bg-gradient-to-r from-[#7FACB3] via-[#4C7980]/50 to-transparent blur-3xl"
      ></div>
    </div>

    <div class="container mx-auto px-4 relative z-10">
      <!-- Badge -->
      <div class="flex justify-center mb-8">
        <span
          class="inline-flex items-center px-4 py-2 bg-white rounded-full shadow-md text-sm font-medium text-gray-700 border border-gray-100"
        >
          <svg
            class="mr-2 h-2 w-2 text-[#7FACB3]"
            fill="currentColor"
            viewBox="0 0 8 8"
          >
            <circle cx="4" cy="4" r="4" />
          </svg>
          Value
        </span>
      </div>

      <!-- Heading -->
      <h1
        class="text-3xl md:text-5xl font-bold text-gray-900 max-w-4xl mx-auto leading-tight mb-12 px-4"
      >
        Crafting exceptional, tech powered strategies that
        <br class="hidden sm:block" />
        deliver real impact.
      </h1>

      <!-- Values Pills -->
      <div class="flex flex-col items-center gap-4 md:gap-5">
        <!-- First row: 3 pills -->
        <div class="flex flex-wrap justify-center gap-3 md:gap-4">
          <div
            v-for="value in values.slice(0, 3)"
            :key="value.id"
            class="flex items-center gap-3 px-5 py-3 rounded-full shadow-sm bg-white/90 backdrop-blur-sm border border-gray-100 hover:shadow-md transition-shadow"
          >
            <span
              :class="`flex items-center justify-center h-10 w-10 rounded-full ${value.color}`"
            >
              <component :is="value.icon" class="h-5 w-5 text-gray-600" />
            </span>
            <span class="text-base font-medium text-gray-800 pr-1">{{
              value.text
            }}</span>
          </div>
        </div>

        <!-- Second row: 2 pills -->
        <div class="flex flex-wrap justify-center gap-3 md:gap-4">
          <div
            v-for="value in values.slice(3, 5)"
            :key="value.id"
            class="flex items-center gap-3 px-5 py-3 rounded-full shadow-sm bg-white/90 backdrop-blur-sm border border-gray-100 hover:shadow-md transition-shadow"
          >
            <span
              :class="`flex items-center justify-center h-10 w-10 rounded-full ${value.color}`"
            >
              <component :is="value.icon" class="h-5 w-5 text-gray-600" />
            </span>
            <span class="text-base font-medium text-gray-800 pr-1">{{
              value.text
            }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
