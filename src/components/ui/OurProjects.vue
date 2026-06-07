<script setup>
import { ref, onMounted } from "vue";

const projects = ref([]);
const loading = ref(true);
const error = ref(null);

onMounted(async () => {
    try {
        const res = await fetch("https://api.nirmanakreasiteknologi.com/project"); 
        const json = await res.json();  

        // Jika response berupa { data: [...] }
        if (Array.isArray(json)) {
        projects.value = json;
        } else if (Array.isArray(json.data)) {
        projects.value = json.data;
        } else {
        console.warn("Format response tidak dikenali:", json);
        projects.value = [];
        }
    } catch (err) {
        console.error("Failed to fetch projects", err);
        error.value = "Gagal mengambil data dari server";
    } finally {
        loading.value = false;
    }
});
</script>

<template>
    <section id="projects" class="w-full py-20 bg-white">
        <div class="max-w-7xl mx-auto px-4 text-center">

            <h2 class="text-3xl md:text-4xl font-semibold mb-12">
            Real Projects. Real People. Real Impact.
            </h2>

            <!-- Loading -->
            <div v-if="loading" class="text-gray-500">Loading projects...</div>

            <!-- Error -->
            <div v-if="error" class="text-red-500">{{ error }}</div>

            <!-- Project Grid -->
            <div v-if="!loading && !error" class="grid md:grid-cols-2 gap-10">
            <div
                v-for="project in projects"
                :key="project.id"
                class="rounded-2xl overflow-hidden shadow-sm p-6 bg-gray-50 flex flex-col justify-between"
            >
                <div>
                    <!-- Image -->
                    <a
                    v-if="project.project_url"
                    :href="project.project_url"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="block overflow-hidden rounded-xl mb-6 group cursor-pointer"
                    >
                    <img
                        :src="project.image_url"
                        alt="project preview"
                        class="w-full object-cover rounded-xl transition-transform duration-300 hover:scale-105"
                    />
                    </a>
                    <img
                    v-else
                    :src="project.image_url"
                    alt="project preview"
                    class="w-full rounded-xl mb-6 object-cover"
                    />

                    <!-- Title -->
                    <h3 class="text-lg font-semibold mb-2 text-center">
                    <a
                        v-if="project.project_url"
                        :href="project.project_url"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="text-blue-600 hover:text-blue-800 hover:underline inline-flex items-center gap-1.5 transition-colors cursor-pointer"
                    >
                        {{ project.title || project.name }}
                        <svg
                        class="w-4 h-4 text-blue-500"
                        fill="none"
                        stroke="currentColor"
                        stroke-width="2"
                        viewBox="0 0 24 24"
                        >
                        <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 6H5.25A2.25 2.25 0 003 8.25v10.5A2.25 2.25 0 005.25 21h10.5A2.25 2.25 0 0018 18.75V10.5m-10.5 6L21 3m0 0h-5.25M21 3v5.25" />
                        </svg>
                    </a>
                    <span v-else>
                        {{ project.title || project.name }}
                    </span>
                    </h3>

                    <!-- Description -->
                    <p class="text-gray-600 text-sm mb-4 text-center">
                    {{ project.description || project.desc }}
                    </p>
                </div>

                <!-- Tags -->
                <div class="flex flex-wrap gap-3 justify-center text-sm text-gray-500 mt-2">
                <span
                    v-for="service in (project.services || [])"
                    :key="service"
                    class="px-3 py-1 bg-white border rounded-full"
                >
                    {{ service }}
                </span>
                </div>

            </div>
            </div>

        </div>
    </section>
</template>
