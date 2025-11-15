<script setup>
import { ref } from "vue";
import AboutUs from "./components/ui/AboutUs.vue";
import ContactUs from "./components/ui/ContactUs.vue";
import Footer from "./components/ui/Footer.vue";
import Jumbotron from "./components/ui/Jumbotron.vue";
import Navbar from "./components/ui/Navbar.vue";
import OurProjects from "./components/ui/OurProjects.vue";
import Value from "./components/ui/Value.vue";
import Vision from "./components/ui/Vision.vue";
import OurServices from "./components/ui/OurServices.vue";

// Refs for each section
const homeRef = ref(null);
const aboutUsRef = ref(null);
const ourProjectsRef = ref(null);
const valueRef = ref(null);
const visionRef = ref(null);
const serviceRef = ref(null);
</script>

<template>
  <!-- Pass all refs as props to the Navbar -->
  <Navbar
    :homeRef="homeRef"
    :aboutUsRef="aboutUsRef"
    :corePrinciplesRef="corePrinciplesRef"
    :whatMakesUsDifferentRef="whatMakesUsDifferentRef"
    :ourProjectsRef="ourProjectsRef"
    :contactUsRef="contactUsRef"
  />

  <main>
    <Jumbotron ref="homeRef" />
    <AboutUs ref="aboutUsRef" />
    <Value ref="valueRef" />
    <Vision ref="visionRef" />
    <OurServices ref="serviceRef" />
    <OurProjects ref="ourProjectsRef" />
    <ContactUs ref="contactUsRef" />
  </main>

  <Footer />
</template>
