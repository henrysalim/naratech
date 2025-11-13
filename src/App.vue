<script setup>
import { ref } from "vue";
import AboutUs from "./components/ui/AboutUs.vue";
import ContactUs from "./components/ui/ContactUs.vue";
import CorePrinciples from "./components/ui/CorePrinciples.vue";
import Footer from "./components/ui/Footer.vue";
import Jumbotron from "./components/ui/Jumbotron.vue";
import Navbar from "./components/ui/Navbar.vue";
import OurProjects from "./components/ui/OurProjects.vue";
import WhatMakesUsDifferent from "./components/ui/WhatMakesUsDifferent.vue";

// Refs for each section
const homeRef = ref(null);
const aboutUsRef = ref(null);
const corePrinciplesRef = ref(null);
const whatMakesUsDifferentRef = ref(null);
const ourProjectsRef = ref(null);
const contactUsRef = ref(null);
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
    <CorePrinciples ref="corePrinciplesRef" />
    <WhatMakesUsDifferent ref="whatMakesUsDifferentRef" />
    <OurProjects ref="ourProjectsRef" />
    <ContactUs ref="contactUsRef" />
  </main>

  <Footer />
</template>
