<script setup>
import { ref } from 'vue';

const activeIndex = ref(0);

const faqs = ref([
    {
        question: 'What is NARATECH and what services offer?',
        answer: 'NARATECH is a technology and digital marketing company dedicated to helping businesses grow through innovation, strategy, and data-driven solutions.',
    },
    {
        question: 'How long does it take to complete a typical project?',
        answer: 'The timeline for a typical project varies depending on its scope and complexity. After our initial consultation, we will provide you with a detailed project timeline.',
    },
    {
        question: 'How can I get in touch or request a consultation?',
        answer: 'You can easily get in touch with us by visiting our "Contact Us" page and filling out the inquiry form. We look forward to hearing from you!',
    },
    {
        question: 'How much services cost?',
        answer: 'Our service costs are tailored to the specific needs of each project. We offer a free consultation to discuss your requirements and provide a detailed, no-obligation quote.',
    },
    ]);

    const toggleAccordion = (index) => {
    if (activeIndex.value === index) {
        activeIndex.value = null;
    } else {
        activeIndex.value = index;
    }
};
</script>

<template>
    <div id="faq" class="bg-white min-h-screen py-16 sm:py-24">
        <div class="mx-auto max-w-3xl px-4 sm:px-6 lg:px-8">
        
        <div class="text-center">
            <span class="inline-flex items-center rounded-full bg-gray-100 px-3 py-1 text-sm font-medium text-gray-700">
            <svg class="mr-1.5 h-2 w-2 text-[#7FACB3]" fill="currentColor" viewBox="0 0 8 8">
                <circle cx="4" cy="4" r="3" />
            </svg>
            FAQ
            </span>
            <h2 class="mt-4 text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">
            Everything You Need to Know About Our Services
            </h2>
        </div>

        <div class="mt-12">
            <div class="divide-y divide-gray-200">
            
            <div v-for="(faq, index) in faqs" :key="index" class="py-6">
                <button 
                @click="toggleAccordion(index)" 
                class="flex w-full items-center justify-between text-left text-gray-900"
                :aria-expanded="activeIndex === index"
                :aria-controls="'faq-answer-' + index"
                >
                <span class="text-lg font-medium">{{ faq.question }}</span>
                <span class="ml-6 flex h-7 items-center">
                    <svg 
                    class="h-6 w-6 transform transition-transform duration-300"
                    :class="{'rotate-180': activeIndex === index}"
                    xmlns="http://www.w3.org/2000/svg" 
                    fill="none" 
                    viewBox="0 0 24 24" 
                    stroke-width="1.5" 
                    stroke="currentColor"
                    >
                    <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
                    </svg>
                </span>
                </button>
                
                <div
                :id="'faq-answer-' + index"
                class="grid overflow-hidden transition-all duration-300 ease-in-out"
                :class="activeIndex === index ? 'grid-rows-[1fr] opacity-100' : 'grid-rows-[0fr] opacity-0'"
                >
                <div class="min-h-0">
                    <div class="pt-4">
                    <div class="p-4 bg-gray-50 rounded-lg">
                        <p class="text-base text-gray-700">
                        {{ faq.answer }}
                        </p>
                    </div>
                    </div>
                </div>
                </div>
            </div>
            </div>
        </div>

        </div>
    </div>
</template>