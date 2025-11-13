<script setup>
import SectionHeading from "./SectionHeading.vue";
</script>

<template>
  <main class="max-w-6xl mx-10 lg:mx-auto h-screen py-10">
    <section id="about-us">
      <SectionHeading title="Get In Touch" />

      <!-- Contact Us Section -->
      <div
        class="grid lg:grid-cols-2 gap-12 rounded-xl shadow-3xl overflow-hidden mt-16"
      >
        <!-- Left: Contact Details & Info -->
        <div class="space-y-8">
          <h3 class="text-3xl font-bold mb-2">Let's Start a Project</h3>
          <p class="text-lg">
            Ready to elevate your business? Contact our team today to discuss
            how NARATECH can become your strategic partner in digital
            transformation.
          </p>

          <div class="space-y-6">
            <div class="flex items-start space-x-4">
              <svg
                class="w-6 h-6 shrink-0 mt-1"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
                ></path>
              </svg>
              <div>
                <h4 class="font-semibold">Email Us</h4>
                <p>Coming Soon</p>
              </div>
            </div>
            <div class="flex items-start space-x-4">
              <svg
                class="w-6 h-6 shrink-0 mt-1"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.828 0l-4.243-4.243a8 8 0 1111.314 0z"
                ></path>
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"
                ></path>
              </svg>
              <div>
                <h4 class="font-semibold">Office Address</h4>
                <p>Coming Soon</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Right: Contact Form -->
        <form class="space-y-6">
          <div>
            <label
              for="name"
              class="block text-sm font-medium text-gray-600 mb-2"
              >Full Name</label
            >
            <input
              type="text"
              id="name"
              name="name"
              class="w-full p-3 rounded-lg border border-gray-700 focus:border-accent focus:ring focus:ring-accent/50"
              placeholder="John Doe"
            />
          </div>
          <div>
            <label
              for="email"
              class="block text-sm font-medium text-gray-600 mb-2"
              >Email Address</label
            >
            <input
              type="email"
              id="email"
              name="email"
              class="w-full p-3 rounded-lg border border-gray-700 focus:border-accent focus:ring focus:ring-accent/50"
              placeholder="you@company.com"
            />
          </div>
          <div>
            <label
              for="message"
              class="block text-sm font-medium text-gray-600 mb-2"
              >Your Message</label
            >
            <textarea
              id="message"
              name="message"
              rows="4"
              class="w-full p-3 rounded-lg border border-gray-700 focus:border-accent focus:ring focus:ring-accent/50"
              placeholder="Tell us about your project..."
            ></textarea>
          </div>
          <button
            type="submit"
            class="w-full px-6 py-3 hover:cursor-pointer hover:bg-gray-600 hover:text-white font-semibold rounded-lg bg-accent shadow-md transition duration-300 hover:bg-opacity-80"
          >
            Send Message
          </button>
        </form>
      </div>
    </section>
  </main>
</template>
