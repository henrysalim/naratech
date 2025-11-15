<script setup>
import { ref, onMounted } from "vue";


const projects = ref([]);


onMounted(async () => {
try {
const res = await fetch("https://api.yourcms.com/projects");
projects.value = await res.json();
} catch (err) {
console.error("Failed to fetch projects", err);
}
});
</script>

<template>
<section class="w-full py-20 bg-white">
<div class="max-w-7xl mx-auto px-4 text-center">
<h2 class="text-3xl md:text-4xl font-semibold mb-12">Real Projects. Real People. Real Impact.</h2>


<div class="grid md:grid-cols-2 gap-10">
<div
v-for="project in projects"
:key="project.id"
class="rounded-2xl overflow-hidden shadow-sm border p-6 bg-gray-50"
>
<img
:src="project.image"
alt="project preview"
class="w-full rounded-xl mb-6 object-cover"
/>


<h3 class="text-lg font-semibold mb-2">{{ project.title }}</h3>
<p class="text-gray-600 text-sm mb-4">{{ project.description }}</p>


<div class="flex flex-wrap gap-3 text-sm text-gray-500">
<span
v-for="tag in project.tags"
:key="tag"
class="px-3 py-1 bg-white border rounded-full"
>
{{ tag }}
</span>
</div>
</div>
</div>
</div>
</section>
</template>