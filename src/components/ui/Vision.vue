<script setup>
import { Target, Handshake, TrendingUp, Sparkles } from 'lucide-vue-next';

const visions = [
    {
        id: 1,
        icon: Target,
        title: 'To deliver IT solutions and digital strategies that are effective, efficient, and results-oriented.'
    },
    {
        id: 2,
        icon: Handshake,
        title: 'To build long-term partnerships founded on trust and collaboration.'
    },
    {
        id: 3,
        icon: TrendingUp,
        title: 'To enhance business competitiveness through relevant and sustainable technological innovation.'
    },
    {
        id: 4,
        icon: Sparkles,
        title: 'To provide added value for clients through professional services that adapt to the changing times.'
    }
];
</script>

<template>
    <section class="relative w-full py-16 md:py-24 bg-gradient-to-b from-white via-gray-50/30 to-white overflow-hidden">
        <!-- Background dot pattern -->
        <div 
        class="absolute inset-0 w-full h-full opacity-20 pointer-events-none"
        style="
            background-image: radial-gradient(circle, #e2e8f0 1px, transparent 1px);
            background-size: 24px 24px;
            background-position: center center;
        "
        ></div>
        
        <div class="container mx-auto px-4 relative z-10">
        <!-- Badge -->
        <div class="flex justify-center mb-8">
            <span class="inline-flex items-center px-4 py-2 bg-white rounded-full shadow-md text-sm font-medium text-gray-700 border border-gray-100">
            <svg class="mr-2 h-2 w-2 text-[#7FACB3]" fill="currentColor" viewBox="0 0 8 8">
                <circle cx="4" cy="4" r="4" />
            </svg>
            Vision
            </span>
        </div>

        <!-- Heading -->
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 text-center mb-12 md:mb-16">
            A Clear Vision. A Purposeful Mission.
        </h2>
        
        <!-- Vision Cards Grid -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 max-w-7xl mx-auto">
            <div 
            v-for="vision in visions" 
            :key="vision.id"
            class="group bg-white rounded-2xl p-6 shadow-sm border border-gray-100 hover:shadow-md transition-all duration-300 hover:-translate-y-1"
            >
            <!-- Icon -->
            <div class="flex justify-center mb-6">
                <div class="flex items-center justify-center h-16 w-16 rounded-full bg-linear-to-b from-[#4C7980]/50 to-[#9FC1C6]/50 transition-colors">
                <component :is="vision.icon" class="h-8 w-8 text-[#4C7980]" :stroke-width="1.5" />
                </div>
            </div>
            
            <!-- Text -->
            <p class="text-center text-sm md:text-base text-gray-700 leading-relaxed">
                {{ vision.title }}
            </p>
            </div>
        </div>
        </div>
    </section>
</template>