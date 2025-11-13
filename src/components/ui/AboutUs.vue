<script setup>
import AboutUsImage from '@/assets/AboutUs.png';

</script>

<template>
  <main class="max-w-6xl mx-10 lg:mx-auto min-h-screen pt-32 md:py-10">
    <section id="about-us">
      <div class="bg-white py-16 lg:py-24">
        <div class="container mx-auto px-4 max-w-screen-xl">
          <div class="flex flex-col lg:flex-row items-center gap-12 lg:gap-16">
            <div class="lg:w-1/2">
              <img :src="AboutUsImage" alt="About Naratech" class="rounded-lg w-full max-w-md mx-auto">
            </div>
            <div class="lg:w-1/2 flex flex-col items-start text-left">
              <span class="inline-flex items-center gap-2 rounded-full bg-gray-100 px-4 py-1 mb-4">
                <span class="w-2 h-2 bg blue-500 rounded-full"></span>
                <span class="text-sm font-medium text-gray-700">About Us</span>
              </span>

              <h1 class="text-3xl lg:text-4xl font-bold text-gray-900 mb-6">
                Building Trust Through Technology and Strategy
              </h1>

              <p class="text-gray-600 text-base lg:text-lg leading-relaxed mb-8">
                NARATECH is a technology and digital marketing company committed to driving business transformation through innovation and integrity.We provide end-to-end digital solutions, from IT systems and strategy to marketing execution designed to help businesses grow efficiently and sustainably
              </p>

              <button class="bg-slate-500 text-white font-semibold px-6 py-3 rounded-lg shadow-md hover:bg-slate-600 transition duration-300 mb-12">
                Book a Call
              </button>

              <div class="flex flex-row flex-wrap gap-8 sm:gap-12">
                <div class="text-left">
                  <span class="block text-4xl font-bold text-gray-900">100+</span>
                  <span class="block text-sm text-gray-500 mt-1">Projects Completed</span>
                </div>

                <div class="text-left">
                  <span class="block text-4xl font-bold text-gray-900">5+</span>
                  <span class="block text-sm text-gray-500 mt-1">Years Of Experience</span>
                </div>

                <div class="text-left">
                  <span class="block text-4xl font-bold text-gray-900">500+</span>
                  <span class="block text-sm text-gray-500 mt-1">Happy Costumer</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>