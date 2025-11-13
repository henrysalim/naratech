<script setup>
import SectionHeading from "./SectionHeading.vue";
import Pill from "../Pill.vue";

let projects = [
  {
    title: "Informatics UMN Website",
    description:
      "To serve as the primary digital interface and information hub for the Universitas Multimedia Nusantara (UMN) Informatics Undergraduate Program, aiming to attract prospective students, support current students, and showcase the program's international standard of education and research achievements.",
    techStacks: ["Laravel", "TailwindCSS", "Bootstrap", "MySQL"],
    sourceCode: "",
    liveDemo: "https://inf.umn.ac.id",
    imagePreview: "/assets/projects/webInf.webp",
  },
];
</script>

<template>
  <main class="max-w-6xl mx-10 lg:mx-auto min-h-screen py-10">
    <section id="about-us">
      <SectionHeading title="Our Projects" />
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="data in projects"
          className="flex flex-col h-full bg-gray-50 rounded-lg overflow-hidden shadow-lg"
        >
          <img
            :src="[data.imagePreview]"
            :alt="[data.title]"
            class="object-cover"
          />
          <div className="p-6 flex-grow">
            <h3 className="text-xl font-semibold mb-3">{{ data.title }}</h3>
            <div className="flex flex-wrap gap-2 mb-4">
              <Pill v-for="tStack in data.techStacks">{{ tStack }}</Pill>
            </div>
            <p className="text-sm">{{ data.description }}</p>
          </div>
          <div className="p-6 bg-gray-100/75 flex justify-end gap-4">
            <a
              :href="[data.sourceCode != '' ? data.sourceCode : '#']"
              target="_blank"
              rel="noopener noreferrer"
              className="inline-flex items-center gap-2 text-sm font-medium text-gray-400 hover:text-gray-600 transition-colors"
            >
              <GithubIcon className="h-4 w-4" />
              Source Code
            </a>
            <a
              :href="[data.liveDemo != '' ? data.liveDemo : '#']"
              target="_blank"
              rel="noopener noreferrer"
              className="inline-flex items-center gap-2 text-sm font-medium text-gray-400 hover:text-gray-600 transition-colors"
            >
              <ExternalLinkIcon className="h-4 w-4" />
              Live Demo
            </a>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>
