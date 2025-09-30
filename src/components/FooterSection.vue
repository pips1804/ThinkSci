<template>
  <footer
    class="bg-[#116530] text-white py-16 px-4 transition-colors duration-300 relative overflow-hidden"
  >
    <!-- Background Pattern -->
    <div class="absolute inset-0 opacity-10">
      <div
        class="absolute inset-0"
        style="
          background-image: radial-gradient(
            circle at 4px 4px,
            currentColor 1px,
            transparent 0
          );
          background-size: 60px 60px;
        "
      ></div>
    </div>

    <div class="max-w-7xl mx-auto relative z-10">
      <div class="grid md:grid-cols-4 gap-12">
        <!-- Logo and Description -->
        <div class="md:col-span-2">
          <div class="flex items-center space-x-3 mb-6">
            <div
              class="w-12 h-12 bg-[#FFCC1D] rounded-xl flex items-center justify-center shadow-lg"
            >
              <Atom class="w-7 h-7 text-[#116530] animate-spin-slow" />
            </div>
            <span class="text-3xl font-bold text-[#FFCC1D]">ThinkSci</span>
          </div>
          <p class="text-gray-300 mb-8 max-w-md text-lg leading-relaxed">
            Turn physics into play! Explore Force, Motion & Energy through our
            gamified Android app with video lessons, collectible badges, and a
            virtual pet companion - all available offline.
          </p>
          <!-- <div class="flex space-x-4">
            <button
              v-for="social in footerSocials"
              :key="social.name"
              class="p-3 bg-[#FFCC1D] rounded-xl hover:bg-yellow-300 transition-all duration-500 hover:scale-110 hover:-translate-y-1 shadow-lg hover:shadow-xl"
              :aria-label="social.name"
            >
              <component :is="social.icon" class="w-6 h-6 text-[#116530]" />
            </button>
          </div> -->
        </div>

        <!-- Quick Links -->
        <div>
          <h4 class="text-[#FFCC1D] font-bold text-xl mb-6">Quick Links</h4>
          <ul class="space-y-4">
            <li v-for="link in footerLinks" :key="link.text">
              <a
                :href="link.href"
                class="text-gray-300 hover:text-[#FFCC1D] transition-all duration-500 text-lg hover:translate-x-2 inline-block"
              >
                {{ link.text }}
              </a>
            </li>
          </ul>
        </div>

        <!-- Project Adviser -->
        <div>
          <h4 class="text-[#FFCC1D] font-bold text-xl mb-6">Project Adviser</h4>
          <ul class="space-y-4">
            <li class="flex flex-col">
              <span class="text-gray-300 text-lg font-semibold"
                >Florante Pangilinan</span
              >
              <p class="text-gray-400 text-base leading-relaxed">
                Our dedicated adviser who guided and supported us throughout the
                development of this project.
              </p>
            </li>
          </ul>
        </div>
      </div>

      <div class="border-t border-gray-600/30 mt-4 pt-4 text-center">
        <p class="text-gray-300 text-lg">
          © 2024 ThinkSci. All rights reserved.
        </p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import {
  Atom,
  Facebook,
  Twitter,
  Instagram,
  Mail,
  Phone,
  MapPin,
} from "lucide-vue-next";

// Data
const footerSocials = [
  { name: "Facebook", icon: Facebook },
  { name: "Twitter", icon: Twitter },
  { name: "Instagram", icon: Instagram },
];

const footerLinks = [
  { href: "#hero", text: "Home" },
  { href: "#about", text: "About" },
  { href: "#developers", text: "Team" },
  //   { href: "#", text: "Privacy Policy" },
];

const contactInfo = [
  { type: "email", icon: Mail, value: "thinksci@gmail.com" },
  { type: "phone", icon: Phone, value: "09936840763" },
  { type: "address", icon: MapPin, value: "Marilao, Bulacan" },
];
</script>

<style scoped>
@keyframes spin-slow {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.animate-spin-slow {
  animation: spin-slow 20s linear infinite;
}
</style>
