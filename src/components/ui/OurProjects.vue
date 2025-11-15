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
                class="rounded-2xl overflow-hidden shadow-sm  p-6 bg-gray-50"
            >

                <!-- Image -->
                <img
                :src="project.image_url"
                alt="project preview"
                class="w-full rounded-xl mb-6 object-cover"
                />

                <!-- Title -->
                <h3 class="text-lg font-semibold mb-2">
                {{ project.title || project.name }}
                </h3>

                <!-- Description -->
                <p class="text-gray-600 text-sm mb-4">
                {{ project.description || project.desc }}
                </p>

                <!-- Tags -->
                <div class="flex flex-wrap gap-3 text-sm text-gray-500">
                <span
                    v-for="service in (project.services || [])"
                    :key="tag"
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
