<script setup>
import { ref, onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollToPlugin } from "gsap/ScrollToPlugin";

// Register GSAP plugin
onMounted(() => {
  gsap.registerPlugin(ScrollToPlugin);
});

// Define props to accept refs from App.vue
const props = defineProps({
  homeRef: Object,
  aboutUsRef: Object,
  corePrinciplesRef: Object,
  whatMakesUsDifferentRef: Object,
  ourProjectsRef: Object,
  contactUsRef: Object,
});

// State for mobile menu
let isNavbarOpened = ref(false);
let currentSection = ref("home"); // You'll need to update this logic, e.g., with IntersectionObserver

const closeMobile = () => (isNavbarOpened.value = false);

// GSAP Smooth Scroll Function
const scrollTo = (targetRef) => {
  if (!targetRef || !(targetRef.value?.$el || targetRef.value)) {
    console.warn("Scroll target ref is not available:", targetRef);
    return;
  }

  // When a ref is on a component, the element is accessed via .$el
  // If it's on a plain element, it's just .value
  const el = targetRef.value.$el || targetRef.value;

  if (el) {
    // Calculate offset: 50px top margin + nav height + 20px buffer
    // Adjust '140' (desktop) and '90' (mobile) as needed.
    const desktopOffset = 140;
    const mobileOffset = 90;

    const targetY =
      el.offsetTop - (window.innerWidth >= 1024 ? desktopOffset : mobileOffset);

    gsap.to(window, {
      duration: 1.0,
      scrollTo: {
        y: targetY,
        autoKill: false,
      },
      ease: "power2.out",
    });
  } else {
    console.error("Could not find element to scroll to.");
  }
};
</script>

<template>
  <nav
    class="fixed z-[99999] top-5 left-4 right-4 rounded-full border border-gray-100 bg-white/80 backdrop-blur-md shadow-lg lg:top-[50px] lg:w-full lg:max-w-6xl lg:left-1/2 lg:-translate-x-1/2"
  >
    <div class="flex flex-row justify-between items-center w-full px-8 py-3">
      <!-- naratech icon -->
      <a
        href="/"
        @click.prevent="scrollTo(props.homeRef)"
        class="shrink-0 inline-flex items-center space-x-2"
      >
        <img
          src="/assets/NaratechLogoWithText.png"
          class="h-10 w-auto"
          alt="Naratech"
        />
      </a>

      <!-- menu lists -->
      <ul
        class="list-none hidden lg:flex flex-row gap-10 text-gray-700 font-medium"
      >
        <li
          :class="[currentSection == 'home' ? 'font-bold text-black' : '']"
          @click="scrollTo(props.homeRef)"
          class="hover:cursor-pointer hover:text-black transition-colors"
        >
          Home
        </li>
        <li
          @click="scrollTo(props.aboutUsRef)"
          class="hover:cursor-pointer hover:text-black transition-colors"
        >
          About Us
        </li>
        <li
          @click="scrollTo(props.whatMakesUsDifferentRef)"
          class="hover:cursor-pointer hover:text-black transition-colors"
        >
          Our Services
        </li>
        <li
          @click="scrollTo(props.ourProjectsRef)"
          class="hover:cursor-pointer hover:text-black transition-colors"
        >
          Our Works
        </li>
      </ul>

      <a
        href="#"
        @click.prevent="scrollTo(props.contactUsRef)"
        class="hidden lg:block px-6 py-3 rounded-full font-semibold transition-all ease-in-out duration-300 cta-btn hover:shadow-md hover:cursor-pointer"
      >
        Let's Collaborate
      </a>

      <!-- Mobile Menu Button -->
      <button
        class="inline-flex lg:hidden items-center justify-center rounded-xl p-2 ring-1 ring-gray-200"
        @click="isNavbarOpened = !isNavbarOpened"
        :aria-expanded="isNavbarOpened"
        aria-controls="mobile-nav"
      >
        <img src="/src/components/icons/hamburger.svg" />
      </button>
    </div>

    <div
      id="mobile-nav"
      class="lg:hidden z-9999 overflow-hidden transition-[max-height] duration-300"
      :style="{ maxHeight: isNavbarOpened ? '600px' : '0px' }"
    >
      <div class="mx-auto max-w-6xl px-6 pb-6">
        <ul
          class="flex flex-col gap-1 rounded-2xl border border-gray-100 bg-white p-2 shadow-sm"
        >
          <li
            @click="
              closeMobile();
              scrollTo(props.homeRef);
            "
            class="block rounded-xl px-3 py-2 hover:bg-gray-50"
          >
            Home
          </li>
          <li
            @click="
              closeMobile();
              scrollTo(props.aboutUsRef);
            "
            class="block rounded-xl px-3 py-2 hover:bg-gray-50"
          >
            About Us
          </li>
          <li
            @click="
              closeMobile();
              scrollTo(props.whatMakesUsDifferentRef);
            "
            class="block rounded-xl px-3 py-2 hover:bg-gray-50"
          >
            Our Services
          </li>
          <li
            @click="
              closeMobile();
              scrollTo(props.ourProjectsRef);
            "
            class="block rounded-xl px-3 py-2 hover:bg-gray-50"
          >
            Our Works
          </li>
          <li
            @click="
              closeMobile();
              scrollTo(props.contactUsRef);
            "
            class="block rounded-xl px-3 py-2 hover:bg-gray-50 text-teal-700 font-medium"
          >
            Let's Collaborate
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
