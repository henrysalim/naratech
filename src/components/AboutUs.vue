<script setup>
import SectionHeading from './SectionHeading.vue';

</script>

<template>
  <main class="max-w-6xl mx-10 lg:mx-auto h-screen py-10">
    <section id="about-us">
      <SectionHeading title="About Us" />
      <p class="text-md">
        PT Nirwana Kreasi Teknologi (NARATECH) is a company specializing in IT
        Solutions and Digital Marketing, established in 2025 with a commitment
        to delivering meaningful and sustainable digital solutions. We believe
        that technology is not just about systems and devices, but about how
        innovation can unlock new opportunities for businesses to grow and
        connect with the world more intelligently. NARATECH serves as a
        strategic partner for companies aiming for digital transformation. By
        integrating technical proficiency, creativity, and deep market
        understanding, we create customized solutions to help clients achieve
        measurable and tangible results.
      </p>
    </section>
    <section
      id="vision-mission"
      class="grid grid-cols-1 lg:grid-cols-2 gap-8 mt-10"
    >
      <div
        id="vision"
        class="p-6 rounded-xl shadow-xl"
      >
        <h3 class="mb-4 text-3xl font-semibold text-center">Vision</h3>
        <p>
          To become the most trusted technology and digital marketing company in
          Indonesia, driving digital transformation through innovation,
          integrity, and a positive impact on the business world.
        </p>
      </div>
      <div
        id="mission"
        class="p-6 rounded-xl shadow-xl"
      >
        <h3 class="mb-4 text-3xl font-semibold text-center">Mission</h3>
        <ol>
          <li>
            To deliver effective, efficient, and results-oriented IT solutions
            and digital strategies.
          </li>
          <li>
            To build long-term partnerships based on trust and collaboration.
          </li>
          <li>
            To enhance business competitiveness through relevant and sustainable
            technological innovation.
          </li>
          <li>
            To provide added value to clients through professional services that
            are adaptive to evolving times.
          </li>
        </ol>
      </div>
    </section>
  </main>
</template>
