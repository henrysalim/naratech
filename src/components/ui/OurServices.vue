<script setup>
import { Code, Smartphone, Bug, Search, Headphones, Share2, Megaphone, Palette } from 'lucide-vue-next';

// Data services
const services = [
    { id: 1, icon: Code, title: 'Website Development' },
    { id: 7, icon: Megaphone, title: 'Digital Marketing' },
    { id: 4, icon: Search, title: 'SEO Specialist' },
    { id: 6, icon: Share2, title: 'Social Media Content Specialist' },
    { id: 3, icon: Bug, title: 'Pent Testing Services' },
    { id: 5, icon: Headphones, title: 'KOL Support' },
    { id: 8, icon: Palette, title: 'Graphic Design' },
    { id: 2, icon: Smartphone, title: 'Mobile Development' },
];

const firstSixServices = services.slice(0, 6);
const lastTwoServices = services.slice(6, 8);
</script>

<template>
    <section id="services" class="relative w-full py-16 md:py-24 bg-gradient-to-b from-gray-50 to-white overflow-hidden">
        <div 
        class="absolute inset-0 w-full h-full opacity-20 pointer-events-none"
        style="
            background-image: radial-gradient(circle, #e2e8f0 1px, transparent 1px);
            background-size: 24px 24px;
            background-position: center center;
        "
        ></div>
        
        <div class="container mx-auto px-4 relative z-10">
        <div class="flex justify-center mb-8">
            <span class="inline-flex items-center px-4 py-2 bg-white rounded-full shadow-md text-sm font-medium text-gray-700 border border-gray-100">
            <svg class="mr-2 h-2 w-2 text-[#7FACB3]" fill="currentColor" viewBox="0 0 8 8">
                <circle cx="4" cy="4" r="4" />
            </svg>
            Services
            </span>
        </div>

        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 text-center mb-12 md:mb-16">
            Center of Excellence
        </h2>
        
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6 max-w-6xl mx-auto items-stretch">
            
            <div class="lg:col-span-2 flex flex-col gap-4">
                <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4">
                    <div 
                        v-for="service in firstSixServices" 
                        :key="service.id"
                        class="group relative bg-white rounded-xl p-5 shadow-sm border border-gray-100 hover:shadow-md transition-all duration-300 hover:-translate-y-1 flex items-center gap-3 overflow-hidden"
                    >
                        <div 
                        class="absolute inset-0 opacity-5 pointer-events-none"
                        style="
                            background-image: url('data:image/svg+xml,%3Csvg width=\'100\' height=\'100\' xmlns=\'http://www.w3.org/2000/svg\'%3E%3Cpath d=\'M0,50 Q25,25 50,50 T100,50\' stroke=\'%23cbd5e1\' stroke-width=\'1\' fill=\'none\'/%3E%3Cpath d=\'M0,70 Q25,45 50,70 T100,70\' stroke=\'%23cbd5e1\' stroke-width=\'1\' fill=\'none\' opacity=\'0.5\'/%3E%3C/svg%3E');
                            background-size: 150px 150px;
                            background-position: top right;
                            background-repeat: no-repeat;
                        "
                        ></div>
                        
                        <div class="flex items-center justify-center h-12 w-12 rounded-xl bg-gray-50 group-hover:bg-[#7FACB3]/50 transition-colors flex-shrink-0 relative z-10">
                        <component :is="service.icon" class="h-6 w-6 text-gray-600 group-hover:text-[#4C7980]/50 transition-colors" :stroke-width="1.5" />
                        </div>
                        
                        <h3 class="text-sm font-semibold text-gray-800 leading-tight relative z-10">
                        {{ service.title }}
                        </h3>
                    </div>
                </div>

                <div class="flex flex-wrap justify-center gap-4 w-full h-full">
                    <div 
                        v-for="service in lastTwoServices" 
                        :key="service.id"
                        class="group relative bg-white rounded-xl p-5 shadow-sm border border-gray-100 hover:shadow-md transition-all duration-300 hover:-translate-y-1 flex items-center gap-3 overflow-hidden w-full sm:w-[48%] md:w-[32%]"
                    >
                        <div 
                        class="absolute inset-0 opacity-5 pointer-events-none"
                        style="
                            background-image: url('data:image/svg+xml,%3Csvg width=\'100\' height=\'100\' xmlns=\'http://www.w3.org/2000/svg\'%3E%3Cpath d=\'M0,50 Q25,25 50,50 T100,50\' stroke=\'%23cbd5e1\' stroke-width=\'1\' fill=\'none\'/%3E%3Cpath d=\'M0,70 Q25,45 50,70 T100,70\' stroke=\'%23cbd5e1\' stroke-width=\'1\' fill=\'none\' opacity=\'0.5\'/%3E%3C/svg%3E');
                            background-size: 150px 150px;
                            background-position: top right;
                            background-repeat: no-repeat;
                        "
                        ></div>
                        
                        <div class="flex items-center justify-center h-12 w-12 rounded-xl bg-gray-50 group-hover:bg-[#7FACB3]/50 transition-colors flex-shrink-0 relative z-10">
                        <component :is="service.icon" class="h-6 w-6 text-gray-600 group-hover:text-[#4C7980]/50 transition-colors" :stroke-width="1.5" />
                        </div>
                        
                        <h3 class="text-sm font-semibold text-gray-800 leading-tight relative z-10">
                        {{ service.title }}
                        </h3>
                    </div>
                </div>
            </div>

            <div class="lg:col-span-1 flex flex-col">
                <div class="relative bg-gradient-to-br from-[#4C7980] to-[#7FACB3]/50 rounded-2xl p-8 w-full h-full flex flex-col justify-center items-start text-white shadow-lg hover:shadow-xl transition-shadow overflow-hidden">
                    <div 
                    class="absolute inset-0 opacity-10 pointer-events-none"
                    style="
                        background-image: url('data:image/svg+xml,%3Csvg width=\'200\' height=\'200\' xmlns=\'http://www.w3.org/2000/svg\'%3E%3Cpath d=\'M0,100 Q50,50 100,100 T200,100\' stroke=\'white\' stroke-width=\'2\' fill=\'none\' opacity=\'0.3\'/%3E%3Cpath d=\'M0,120 Q50,70 100,120 T200,120\' stroke=\'white\' stroke-width=\'2\' fill=\'none\' opacity=\'0.2\'/%3E%3Cpath d=\'M0,140 Q50,90 100,140 T200,140\' stroke=\'white\' stroke-width=\'1\' fill=\'none\' opacity=\'0.1\'/%3E%3C/svg%3E');
                        background-size: 300px 300px;
                        background-position: top left;
                        background-repeat: no-repeat;
                    "
                    ></div>
                    
                    <h3 class="text-xl md:text-2xl font-bold mb-4 leading-tight relative z-10">
                    See Our Work in Action.<br>
                    Start Your Creative<br>
                    Journey with Us!
                    </h3>
                    
                    <a href="https://wa.me/62859106612098" type="button" class="mt-4 px-6 py-3 bg-white text-slate-700 rounded-lg font-semibold text-sm hover:bg-gray-100 transition-colors shadow-md hover:shadow-lg relative z-10">
                    Services FAQ
                    </a>
                </div>
            </div>
        </div>
        </div>
    </section>
</template>