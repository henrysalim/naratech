<script setup>
import { onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollToPlugin } from "gsap/ScrollToPlugin";

// Register GSAP plugin (best practice to register whenever used)
onMounted(() => {
  gsap.registerPlugin(ScrollToPlugin);
});

// 1. Definisikan Props (Sama seperti Navbar)
const props = defineProps({
  homeRef: Object,
  aboutUsRef: Object,
  ourServicesRef: Object,
  ourProjectsRef: Object,
  faqRef: Object, // Opsional jika ingin link ke FAQ dari footer
});

// 2. Logic Scroll (Sama seperti Navbar)
const getElementFromRef = (targetRef) => {
  if (!targetRef) return null;
  if (typeof targetRef === "string") {
    return (
      document.getElementById(targetRef) || document.querySelector(targetRef)
    );
  }
  const candidate = targetRef.value ?? targetRef;
  if (candidate && candidate.$el) return candidate.$el;
  if (candidate instanceof Element) return candidate;
  return null;
};

const fallbackIdMap = new Map([
  ["homeRef", "home"],
  ["aboutUsRef", "about-us"],
  ["ourServicesRef", "services"],
  ["ourProjectsRef", "projects"],
]);

const scrollTo = (targetRef, propName = null) => {
  let el = getElementFromRef(targetRef);

  if (!el && propName && fallbackIdMap.has(propName)) {
    const id = fallbackIdMap.get(propName);
    el = document.getElementById(id);
  }

  if (!el) {
    console.warn("Scroll target element not found for:", targetRef);
    return;
  }

  // Offset disesuaikan (Footer biasanya butuh offset yang sama dengan Navbar desktop)
  const offset = 100; 

  const targetY =
    el.getBoundingClientRect().top + window.scrollY - offset;

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
    window.scrollTo({ top: targetY, behavior: "smooth" });
  }
};
</script>

<template>
  <section
    class="relative w-full overflow-hidden bg-gradient-to-br from-[#4C7980] from-30% to-[#7FACB3] py-16 lg:py-0 lg:h-[405px]"
  >
    <img
      src="/assets/footer/dotsRight.svg"
      alt="Dots"
      class="absolute hidden lg:block top-10 right-10 w-1/3 max-w-xs opacity-60"
    />
    
    <img
      src="/assets/footer/wave.svg"
      alt="Waves"
      class="absolute bottom-0 left-0 w-full h-full object-cover opacity-10 mix-blend-overlay"
    />

    <div
      class="relative z-10 mx-auto flex h-full max-w-6xl flex-col items-center px-6 lg:flex-row"
    >
      <div class="relative h-64 w-full lg:h-full lg:w-1/2">
        <img
          src="/assets/footer/dotsLeft.svg"
          alt="Dots"
          class="absolute top-0 left-0 w-1/3 opacity-60 lg:w-auto"
        />
        <img
          src="/assets/footer/footer_person.png"
          alt="Footer person illustration"
          class="absolute bottom-0 left-1/2 h-full w-auto -translate-x-1/2 lg:left-1/4 xl:left-32"
        />
      </div>

      <div
        class="mt-8 flex w-full flex-col items-center text-center lg:mt-0 lg:w-1/2 lg:items-start lg:text-left"
      >
        <h3
          class="mb-8 max-w-md text-3xl font-bold tracking-wider text-white lg:text-4xl"
        >
          Ready to Start Your Digital Transformation?
        </h3>
        
        <!-- Button Contact Us (Direct WhatsApp) -->
        <a
          href="https://wa.me/6285128063897?text=Halo%20Naratech,%20saya%20tertarik%20untuk%20bekerja%20sama."
          target="_blank"
          rel="noopener noreferrer"
          class="block w-52 rounded-2xl bg-white px-10 py-4 text-center font-semibold text-gray-900 transition-transform duration-300 ease-in-out hover:-translate-y-2"
        >
          Contact Us
        </a>
      </div>
    </div>
  </section>

  <footer class="bg-[#263D40] py-10 text-white">
    <div
      class="mx-auto flex max-w-5xl flex-col items-center px-6 text-center text-sm sm:px-8 lg:px-10"
    >
      <img
        src="/assets/footer/naratech_white.png"
        alt="Nusatech Logo"
        class="w-20"
      />
      
      <!-- NAVIGASI FOOTER DENGAN GSAP SCROLL -->
      <ul
        class="mt-7 flex w-full flex-wrap justify-center gap-y-2 gap-x-6 lg:gap-x-10"
      >
        <li>
          <a 
            href="#home" 
            @click.prevent="scrollTo(props.homeRef, 'homeRef')"
            class="font-semibold transition-colors hover:text-gray-300 cursor-pointer"
          >
            Home
          </a>
        </li>
        <li>
          <a 
            href="#about" 
            @click.prevent="scrollTo(props.aboutUsRef, 'aboutUsRef')"
            class="font-semibold transition-colors hover:text-gray-300 cursor-pointer"
          >
            About Us
          </a>
        </li>
        <li>
          <a 
            href="#services" 
            @click.prevent="scrollTo(props.ourServicesRef, 'ourServicesRef')"
            class="font-semibold transition-colors hover:text-gray-300 cursor-pointer"
          >
            Our Services
          </a>
        </li>
        <li>
          <a 
            href="#projects" 
            @click.prevent="scrollTo(props.ourProjectsRef, 'ourProjectsRef')"
            class="font-semibold transition-colors hover:text-gray-300 cursor-pointer"
          >
            Our Projects
          </a>
        </li>
      </ul>

      <div class="mt-7 h-px w-full bg-white/30"></div>

      <div class="mt-7 flex flex-wrap justify-center gap-4 lg:gap-6">
        <!-- Social Media Links (Tetap sama) -->
        <a href="https://wa.me/6285128063897" target="_blank" class="rounded-full bg-[#7FACB3] p-3 transition-transform hover:-translate-y-1">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-phone"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.05 12.05 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.05 12.05 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/></svg>
        </a>
        <a href="#" class="rounded-full bg-[#7FACB3] p-3 transition-transform hover:-translate-y-1">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-facebook"><path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z"/></svg>
        </a>
        <a href="#" class="rounded-full bg-[#7FACB3] p-3 transition-transform hover:-translate-y-1">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-linkedin"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect width="4" height="12" x="2" y="9"/><circle cx="4" cy="4" r="2"/></svg>
        </a>
        <a href="#" class="rounded-full bg-[#7FACB3] p-3 transition-transform hover:-translate-y-1">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-youtube"><path d="M2.5 17a24.12 24.12 0 0 1 0-10 2 2 0 0 1 1.4-1.4 49.56 49.56 0 0 1 16.2 0A2 2 0 0 1 21.5 7a24.12 24.12 0 0 1 0 10 2 2 0 0 1-1.4 1.4 49.55 49.55 0 0 1-16.2 0A2 2 0 0 1 2.5 17"/><path d="m10 15 5-3-5-3z"/></svg>
        </a>
        <a href="#" class="rounded-full bg-[#7FACB3] p-3 transition-transform hover:-translate-y-1">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-instagram"><rect width="20" height="20" x="2" y="2" rx="5" ry="5"/><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"/><line x1="17.5" x2="17.51" y1="6.5" y2="6.5"/></svg>
        </a>
        <a href="#" class="rounded-full bg-[#7FACB3] p-3 transition-transform hover:-translate-y-1">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-mail"><path d="m22 7-8.991 5.727a2 2 0 0 1-2.009 0L2 7"/><rect x="2" y="4" width="20" height="16" rx="2"/></svg>
        </a>
      </div>
      
      <span class="mt-7 font-semibold text-[#94A3B8]"
        >&copy; 2025 Naratech. All Rights Reserved.</span
      >
    </div>
  </footer>
</template>