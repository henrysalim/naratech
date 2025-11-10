<script setup>
import { ref, onMounted, onUnmounted } from "vue"
import { gsap } from "gsap"

const prefix = "Beyond Technology, Towards "
const words = ["Success", "Innovation", "Excellence", "Impact"]

const textRef = ref(null)

onMounted(() => {
  let tl = gsap.timeline({ repeat: -1 })

    tl.to({ len: 0 }, {
    len: prefix.length,
    duration: prefix.length * 0.06,
    ease: "none",
    onUpdate() {
      const length = Math.round(this.targets()[0].len)
      textRef.value.textContent = prefix.substring(0, length)
      cursorRef.value.style.transform = `translateX(${length * 0.62}em)`
    }
  })

  tl.to({}, { duration: 0.5 })
  
  words.forEach((w) => {
    tl.to({ len: 0 }, {
      len: w.length,
      duration: w.length * 0.06,
      ease: "none",
      onUpdate() {
        const length = Math.round(this.targets()[0].len)
        textRef.value.textContent = prefix + w.substring(0, length)
        cursorRef.value.style.transform = `translateX(${(prefix.length + length) * 0.62}em)`
      }
    })

    tl.to({}, { duration: 1 })

    tl.to({ len: w.length }, {
      len: 0,
      duration: w.length * 0.045,
      ease: "none",
      onUpdate() {
        const length = Math.round(this.targets()[0].len)
        textRef.value.textContent = prefix + w.substring(0, length)
        cursorRef.value.style.transform = `translateX(${(prefix.length + length) * 0.62}em)`
      }
    })

    tl.to({}, { duration: 0.15 })
  })
  tl.to({ len: prefix.length }, {
    len: 0,
    duration: prefix.length * 0.05,
    ease: "none",
    onUpdate() {
      const length = Math.round(this.targets()[0].len)
      textRef.value.textContent = prefix.substring(0, length)
      cursorRef.value.style.transform = `translateX(${length * 0.62}em)`
    }
  })

  tl.to({}, { duration: 0.35 })
})

onUnmounted(() => {
  tl?.kill()
})

</script>

<template>
  <main class="text-left h-screen flex max-w-6xl mx-10 lg:mx-auto">
    <header class="relative mt-32">
      <h1 class="text-5xl md:text-6xl lg:text-7xl font-extrabold mb-4">
        Nirmana Kreasi Teknologi
      </h1>
      <h3 class="text-2xl md:text-3xl lg:text-4xl">
        <span ref="textRef"></span>
        <span ref="cursorRef" class="cursor">_</span>
      </h3>
    </header>
  </main>
</template>

<style scoped>
.cursor {
  display: inline-block;
  animation: blink 0.8s infinite alternate;
  margin-left: 4px;
}

@keyframes blink {
  0% { opacity: 0 }
  50% { opacity: 1 }
}
</style>
