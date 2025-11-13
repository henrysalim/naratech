<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { gsap } from "gsap";

const prefix = "We help business navigate digital transformation through ";
const words = ["strategy", "innovation", "measurable results"];

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
</script>

<template>
  <main
    class="bg-linear-to-t from-[#FEFEFF] from-5% to-[#EFF5F6] to-90% relative"
  >
    <section
      id="home"
      class="min-h-screen flex flex-col items-center max-w-6xl mx-10 lg:mx-auto pt-64"
    >
      <h1
        class="pb-2 text-5xl text-center lg:text-6xl xl:text-7xl font-bold tracking-wide bg-clip-text bg-linear-to-r from-[#4C7980] to-[#7FACB3] text-transparent"
      >
        Empowering Business
      </h1>
      <h2
        class="text-xl lg:text-2xl xl:text-3xl font-semibold mt-4 tracking-wider"
      >
        Through Smart Digital Strategy
      </h2>
      <header class="my-6">
        <h4 class="text-lg text-center font-light">
          <span ref="textRef"></span>
          <span ref="cursorRef" class="cursor">_</span>
        </h4>
      </header>

      <a href="" class="cta-btn z-[9999] block font-semibold mt-10"
        >Book a call</a
      >

      <span
        class="w-64 h-12 z-[9999] rounded-4xl border border-white mt-16 md:mt-[120px] lg:mt-[150px] bg-[#EBF1F3] flex justify-center items-center"
        >+10 Happy Customers</span
      >
    </section>

    <img
      src="/assets/jumbotron/right.svg"
      alt="Right backgrund"
      class="w-[80%] lg:w-auto absolute right-0 top-0"
    />
    <img
      src="/assets/jumbotron/left.svg"
      alt="Right backgrund"
      class="w-[80%] lg:w-auto absolute left-0 top-0"
    />
    <img
      src="/assets/jumbotron/greenSquares.svg"
      alt="Right backgrund"
      class="absolute left-4 bottom-16"
    />
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
