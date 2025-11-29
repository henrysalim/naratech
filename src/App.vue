<script setup>
import { ref } from "vue";
import AboutUs from "./components/ui/AboutUs.vue";
import Footer from "./components/ui/Footer.vue";
import Jumbotron from "./components/ui/Jumbotron.vue";
import Navbar from "./components/ui/Navbar.vue";
import OurProjects from "./components/ui/OurProjects.vue";
import Value from "./components/ui/Value.vue";
import Vision from "./components/ui/Vision.vue";
import OurServices from "./components/ui/OurServices.vue";
import FaQ from "./components/ui/FaQ.vue";
import WhatsappFloating from "./components/ui/WhatsappFloating.vue";

// Refs for each section
const homeRef = ref(null);
const aboutUsRef = ref(null);
const ourProjectsRef = ref(null);
const ourServicesRef = ref(null);
const faqRef = ref(null);
const valueRef = ref(null);
const visionRef = ref(null);
</script>

<template>
  <!-- Pass all refs as props to the Navbar -->
  <Navbar
    :homeRef="homeRef"
    :aboutUsRef="aboutUsRef"
    :ourServicesRef="ourServicesRef"
    :ourProjectsRef="ourProjectsRef"
    :faqRef="faqRef"
    :valueRef="valueRef"
    :visionRef="visionRef"
  />

  <main>
    <Jumbotron ref="homeRef" />
    <AboutUs ref="aboutUsRef" />
    <Value ref="valueRef" />
    <Vision ref="visionRef" />
    <OurServices ref="ourServicesRef" />
    <OurProjects ref="ourProjectsRef" />
    <FaQ ref="faqRef" />
  </main>

  <Footer />

  <WhatsappFloating />
</template>
