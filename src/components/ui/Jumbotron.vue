<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { gsap } from "gsap";

const prefix = "Beyond Technology, Towards ";
const words = ["Success", "Innovation", "Excellence", "Impact"];

const textRef = ref(null);
const cursorRef = ref(null);

onMounted(() => {
  let tl = gsap.timeline({ repeat: -1 });

  tl.to(
    { len: 0 },
    {
      len: prefix.length,
      duration: prefix.length * 0.06,
      ease: "none",
      onUpdate() {
        const length = Math.round(this.targets()[0].len);
        textRef.value.textContent = prefix.substring(0, length);
        cursorRef.value.style.transform = `translateX(${length * 0.001}em)`;
      },
    }
  );

  tl.to({}, { duration: 0.5 });

  words.forEach((w) => {
    tl.to(
      { len: 0 },
      {
        len: w.length,
        duration: w.length * 0.06,
        ease: "none",
        onUpdate() {
          const length = Math.round(this.targets()[0].len);
          textRef.value.textContent = prefix + w.substring(0, length);
          cursorRef.value.style.transform = `translateX(${
            (prefix.length + length) * 0.001
          }em)`;
        },
      }
    );

    tl.to({}, { duration: 1 });

    tl.to(
      { len: w.length },
      {
        len: 0,
        duration: w.length * 0.045,
        ease: "none",
        onUpdate() {
          const length = Math.round(this.targets()[0].len);
          textRef.value.textContent = prefix + w.substring(0, length);
          cursorRef.value.style.transform = `translateX(${
            (prefix.length + length) * 0.001
          }em)`;
        },
      }
    );

    tl.to({}, { duration: 0.15 });
  });
  tl.to(
    { len: prefix.length },
    {
      len: 0,
      duration: prefix.length * 0.05,
      ease: "none",
      onUpdate() {
        const length = Math.round(this.targets()[0].len);
        textRef.value.textContent = prefix.substring(0, length);
        cursorRef.value.style.transform = `translateX(${length * 0.001}em)`;
      },
    }
  );

  tl.to({}, { duration: 0.35 });
});

onUnmounted(() => {
  tl?.kill();
});

const coreServices = [
  {
    title: "Website Development",
    description:
      "Building professional websites that are fast, responsive, and easy to manage.",
    icon: "<svg xmlns='http://www.w3.org/2000/svg' width='30' height='30' viewBox='0 0 24 24' fill='none' stroke='currentColor' stroke-width='2' stroke-linecap='round' stroke-linejoin='round' class='lucide lucide-globe-icon lucide-globe'><circle cx='12' cy='12' r='10'/><path d='M12 2a14.5 14.5 0 0 0 0 20 14.5 14.5 0 0 0 0-20'/><path d='M2 12h20'/></svg>",
  },
  {
    title: "Application Development",
    description:
      "Designing web and mobile applications tailored to business needs.",
    icon: "<svg xmlns='http://www.w3.org/2000/svg' width='30' height='30' viewBox='0 0 24 24' fill='none' stroke='currentColor' stroke-width='2' stroke-linecap='round' stroke-linejoin='round' class='lucide lucide-smartphone-icon lucide-smartphone'><rect width='14' height='20' x='5' y='2' rx='2' ry='2'/><path d='M12 18h.01'/></svg>",
  },
  {
    title: "Digital Advertising (Ads Management)",
    description:
      "Managing digital ad campaigns to increase brand awareness and conversions.",
    icon: "<svg xmlns='http://www.w3.org/2000/svg' width='30' height='30' viewBox='0 0 24 24' fill='none' stroke='currentColor' stroke-width='2' stroke-linecap='round' stroke-linejoin='round' class='lucide lucide-megaphone-icon lucide-megaphone'><path d='M11 6a13 13 0 0 0 8.4-2.8A1 1 0 0 1 21 4v12a1 1 0 0 1-1.6.8A13 13 0 0 0 11 14H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2z'/><path d='M6 14a12 12 0 0 0 2.4 7.2 2 2 0 0 0 3.2-2.4A8 8 0 0 1 10 14'/><path d='M8 6v8'/></svg>",
  },
  {
    title: "Search Engine Optimization (SEO)",
    description:
      "Increasing business visibility on search engines to reach the right audience.",
    icon: "<svg xmlns='http://www.w3.org/2000/svg' width='30' height='30' viewBox='0 0 24 24' fill='none' stroke='currentColor' stroke-width='2' stroke-linecap='round' stroke-linejoin='round' class='lucide lucide-scan-search-icon lucide-scan-search'><path d='M3 7V5a2 2 0 0 1 2-2h2'/><path d='M17 3h2a2 2 0 0 1 2 2v2'/><path d='M21 17v2a2 2 0 0 1-2 2h-2'/><path d='M7 21H5a2 2 0 0 1-2-2v-2'/><circle cx='12' cy='12' r='3'/><path d='m16 16-1.9-1.9'/></svg>",
  },
];

onMounted(() => {
  for (let i = 0; i < coreServices.length; i++) {
    document.getElementById("icon," + i).innerHTML = coreServices[i].icon;
  }
});
</script>

<template>
  <main
    style="
      background: url('/assets/jumbotron.webp') no-repeat;
      background-size: cover;
    "
    class="relative"
  >
    <section
      id="home"
      class="text-left min-h-screen flex flex-col max-w-6xl mx-10 lg:mx-auto relative z-[9999]"
    >
      <header class="relative mt-32">
        <h1
          class="text-5xl md:text-6xl lg:text-7xl text-white font-extrabold mb-4"
        >
          Nirmana Kreasi Teknologi
        </h1>
        <h3 class="text-2xl md:text-3xl lg:text-4xl text-white">
          <span ref="textRef"></span>
          <span ref="cursorRef" class="cursor">_</span>
        </h3>
      </header>

      <div
        class="grid grid-cols-2 lg:grid-cols-4 absolute -bottom-20 lg:bottom-32 gap-10"
      >
        <div
          class="p-6 rounded-xl shadow-xl bg-gray-100"
          v-for="(serviceData, idx) in coreServices"
          v-show="idx != 4"
        >
          <div class="flex flex-col items-center justify-center mb-6">
            <span :id="['icon', idx]" class="mb-4 block"></span>
            <h3
              class="text-xl font-bold text-center h-14"
              :class="[idx == 0 ? 'w-3/4' : 'w-full']"
            >
              {{ serviceData.title }}
            </h3>
          </div>
          <p>{{ serviceData.description }}</p>
        </div>
      </div>
    </section>
    <div
      id="jumbotronBackground"
      class="bg-gray-900/25 absolute w-full h-full bottom-0"
    ></div>
  </main>
</template>

<style scoped>
.cursor {
  display: inline-block;
  animation: blink 0.8s infinite alternate;
  margin-left: 4px;
}

@keyframes blink {
  0% {
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
}
</style>
