<script setup>
  import { ref } from 'vue';

  let isNavbarOpened = ref(false);
  let isAboutOpen =ref(false);
  let currentSection = ref("home")

  const closeMobile = () => (isNavbarOpened.value = false);

</script>

<template>
  <nav class="w-full bg-transparent border-b border-gray-100">
    <div class="flex flex-row justify-between items-center p-6 max-w-6xl mx-auto">
      <!-- naratech icon -->
       <a href="/" class="shrink-0 inline-flex items-center space-x-2">
         <img src="/src/assets/logo.svg" class="w-10 h-10" alt="Naratech" />
        </a>
       <ul class="list-none hidden lg:flex flex flex-row gap-10">
          <li :class="[currentSection == 'home' ? 'font-bold' : '']">Home</li>
          <li class="relative hidden lg:block">
            <button
              class="peer inline-flex hover:cursor-pointer items-center gap-2 text-gray-700 focus:text-gray-900"
              aria-haspopup="true"
            >
              About Us
              <svg class="h-4 w-4" viewBox="0 0 20 20" fill="currentColor">
                <path
                  fill-rule="evenodd"
                  d="M5.23 7.21a.75.75 0 011.06.02L10 10.94l3.71-3.71a.75.75 0 111.06 1.06l-4.24 4.24a.75.75 0 01-1.06 0L5.21 8.29a.75.75 0 01.02-1.08z"
                  clip-rule="evenodd"
                />
              </svg>
            </button>

            <div
              class="absolute left-0 top-full w-64 rounded-2xl border border-gray-100 bg-white shadow-xl
                    opacity-0 invisible translate-y-1 transition
                    peer-focus:opacity-100 peer-focus:visible peer-focus:translate-y-0"
            >
              <ul class="py-2 text-sm">
                <li class="block px-4 py-2 hover:bg-gray-50 focus:bg-gray-50 focus:outline-none">
                  Vision &amp; Mission
                </li>
                <li class="block px-4 py-2 hover:bg-gray-50 focus:bg-gray-50 focus:outline-none">
                  Our Core Values
                </li>
                <li class="block px-4 py-2 hover:bg-gray-50 focus:bg-gray-50 focus:outline-none">
                  Our Services
                </li>
                <li  class="block px-4 py-2 hover:bg-gray-50 focus:bg-gray-50 focus:outline-none">
                  What Makes Us Different?
                </li>
              </ul>
            </div>
          </li>

          <li>Contact Us</li>
       </ul>
       <button 
              class="inline-flex lg:hidden items-center justify-center rounded-xl p-2 ring-1 ring-gray-200"
              @click="isNavbarOpened = !isNavbarOpened"
              :aria-expanded="isNavbarOpened"
              :aria-controls="mobile-nav">
          <img src="/src/components/icons/hamburger.svg" />
       </button>
    </div>
    <div
      id="mobile-nav"
      class="lg:hidden overflow-hidden transition-[max-height] duration-300"
      :style="{ maxHeight: isNavbarOpened ? '600px' : '0px' }"
    >
      <div class="mx-auto max-w-6xl px-6 pb-6">
        <ul class="flex flex-col gap-1 rounded-2xl border border-gray-100 bg-white p-2 shadow-sm">
          <li @click="closeMobile" class="block rounded-xl px-3 py-2 hover:bg-gray-50">Home</li>

          <li>
            <button
              class="w-full flex items-center justify-between rounded-xl px-3 py-2 hover:bg-gray-50"
              @click="isAboutOpen = !isAboutOpen"
              :aria-expanded="isAboutOpen"
            >
              <span>About Us</span>
              <svg class="h-4 w-4 transition" :class="isAboutOpen ? 'rotate-180' : ''" viewBox="0 0 20 20" fill="currentColor">
                <path fill-rule="evenodd" d="M5.23 7.21a.75.75 0 011.06.02L10 10.94l3.71-3.71a.75.75 0 111.06 1.06l-4.24 4.24a.75.75 0 01-1.06 0L5.21 8.29a.75.75 0 01.02-1.08z" clip-rule="evenodd"/>
              </svg>
            </button>
            <div
              class="grid transition-[grid-template-rows] duration-300"
              :style="{ gridTemplateRows: isAboutOpen ? '1fr' : '0fr' }"
            >
              <ul class="overflow-hidden pl-3">
                <li @click="closeMobile" class="block rounded-lg px-3 py-2 hover:bg-gray-50">Vision &amp; Mission</li>
                <li @click="closeMobile" class="block rounded-lg px-3 py-2 hover:bg-gray-50">Our Core Values</li>
                <li @click="closeMobile" class="block rounded-lg px-3 py-2 hover:bg-gray-50">Our Services</li>
                <li @click="closeMobile" class="block rounded-lg px-3 py-2 hover:bg-gray-50">What Makes Us Different?</li>
              </ul>
            </div>
          </li>
          <li @click="closeMobile" class="block rounded-xl px-3 py-2 hover:bg-gray-50">Contact Us</li>
        </ul>
      </div>
    </div>
  </nav>
</template>