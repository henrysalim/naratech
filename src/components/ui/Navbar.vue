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
  ourServicesRef: Object,
  ourProjectsRef: Object,
  faqRef: Object,
});

// State for mobile menu
let isNavbarOpened = ref(false);
let currentSection = ref("home"); // You'll need to update this logic, e.g., with IntersectionObserver

const closeMobile = () => (isNavbarOpened.value = false);

// GSAP Smooth Scroll Function
const getElementFromRef = (targetRef) => {
  if (!targetRef) return null;

  // If caller passed a string selector or id
  if (typeof targetRef === "string") {
    return (
      document.getElementById(targetRef) || document.querySelector(targetRef)
    );
  }

  // If a ref object was passed (the common case from App.vue)
  const candidate = targetRef.value ?? targetRef;

  // Component public instance (SFC) - try .$el
  if (candidate && candidate.$el) return candidate.$el;

  // DOM element
  if (candidate instanceof Element) return candidate;

  return null;
};

// Map of known refs to fallback ids (used if a component hasn't exposed its root)
const fallbackIdMap = new Map([
  ["homeRef", "home"],
  ["aboutUsRef", "about-us"],
  ["ourServicesRef", "services"],
  ["ourProjectsRef", "projects"],
  ["faqRef", "faq"],
]);

const scrollTo = (targetRef, propName = null) => {
  let el = getElementFromRef(targetRef);

  // If not found, try fallback by prop name -> id
  if (!el && propName && fallbackIdMap.has(propName)) {
    const id = fallbackIdMap.get(propName);
    el = document.getElementById(id);
  }

  if (!el) {
    console.warn("Scroll target element not found for:", targetRef, propName);
    return;
  }

  const desktopOffset = 140;
  const mobileOffset = 90;

  const targetY =
    el.getBoundingClientRect().top +
    window.scrollY -
    (window.innerWidth >= 1024 ? desktopOffset : mobileOffset);

  try {
    gsap.to(window, {
      duration: 1.0,
      scrollTo: {
        y: targetY,
        autoKill: false,
      },
      ease: "power2.out",
    });
  } catch (err) {
    // If ScrollToPlugin isn't available, fallback to native smooth scroll
    window.scrollTo({ top: targetY, behavior: "smooth" });
  }
};
</script>

<template>
  <nav
    class="fixed z-[99999] top-5 left-4 right-4 lg:top-[50px] lg:w-full lg:max-w-6xl lg:left-1/2 lg:-translate-x-1/2"
  >
    <div
      class="flex flex-row justify-between items-center w-full px-8 py-3 rounded-full border border-gray-100 bg-white/80 backdrop-blur-md shadow-lg"
    >
      <!-- naratech icon -->
      <a
        href="/"
        @click.prevent="scrollTo(props.homeRef, 'homeRef')"
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
          @click="scrollTo(props.homeRef, 'homeRef')"
          class="hover:cursor-pointer hover:text-black transition-colors"
        >
          Home
        </li>
        <li
          @click="scrollTo(props.aboutUsRef, 'aboutUsRef')"
          class="hover:cursor-pointer hover:text-black transition-colors"
        >
          About Us
        </li>
        <li
          @click="scrollTo(props.ourServicesRef, 'ourServicesRef')"
          class="hover:cursor-pointer hover:text-black transition-colors"
        >
          Our Services
        </li>
        <li
          @click="scrollTo(props.ourProjectsRef, 'ourProjectsRef')"
          class="hover:cursor-pointer hover:text-black transition-colors"
        >
          Our Projects
        </li>
      </ul>

      <a
        href="#"
        @click.prevent="scrollTo(props.faqRef, 'faqRef')"
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
              scrollTo(props.homeRef, 'homeRef');
            "
            class="block rounded-xl px-3 py-2 hover:bg-gray-50"
          >
            Home
          </li>
          <li
            @click="
              closeMobile();
              scrollTo(props.aboutUsRef, 'aboutUsRef');
            "
            class="block rounded-xl px-3 py-2 hover:bg-gray-50"
          >
            About Us
          </li>
          <li
            @click="
              closeMobile();
              scrollTo(props.ourServicesRef, 'ourServicesRef');
            "
            class="block rounded-xl px-3 py-2 hover:bg-gray-50"
          >
            Our Services
          </li>
          <li
            @click="
              closeMobile();
              scrollTo(props.ourProjectsRef, 'ourProjectsRef');
            "
            class="block rounded-xl px-3 py-2 hover:bg-gray-50"
          >
            Our Projects
          </li>
          <li
            @click="
              closeMobile();
              scrollTo(props.faqRef, 'faqRef');
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
