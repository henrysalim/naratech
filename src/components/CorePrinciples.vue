<script setup>
import SectionHeading from "./SectionHeading.vue";

let corePrinciples = [
  {
    title: "Integrity",
    description:
      "We uphold honesty and responsibility in every step of our work.",
  },
  {
    title: "Innovation",
    description:
      "We are constantly seeking new ways to create more effective and impactful solutions.",
  },
  {
    title: "Collaboration",
    description:
      "We believe the best results stem from solid teamwork and communication.",
  },
  {
    title: "Excellence",
    description:
      "We are committed to delivering the best results, going beyond merely meeting expectations.",
  },
  {
    title: "Sustainability",
    description:
      "We focus on long-term growth that benefits both our clients and the community.",
  },
];
</script>

<template>
  <main class="max-w-6xl mx-10 lg:mx-auto h-screen py-10">
    <section id="core-principles">
      <SectionHeading title="Our Core Values" />

      <div class="grid grid-cols-1 gap-6 md:grid-cols-2">
        <div
          class="p-6 rounded-xl shadow-xl"
          v-for="(principleData, idx) in corePrinciples"
          v-show="idx != 4"
        >
          <h3 class="mb-4 text-3xl font-semibold text-center">
            {{ principleData.title }}
          </h3>
          <p>{{ principleData.description }}</p>
        </div>
      </div>
      <div class="w-full mt-6">
        <div class="p-6 rounded-xl shadow-xl">
          <h3 class="mb-4 text-3xl font-semibold text-center">
            {{ corePrinciples[4].title }}
          </h3>
          <p class="text-center">{{ corePrinciples[4].description }}</p>
        </div>
      </div>
    </section>
  </main>
</template>
