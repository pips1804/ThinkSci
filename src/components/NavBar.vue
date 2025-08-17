<template>
  <nav
    class="bg-white/80 dark:bg-gray-900/80 backdrop-blur-xl shadow-lg sticky top-0 z-50 transition-all duration-300 border-b border-white/20 dark:border-gray-700/20"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <!-- Logo -->
        <div class="flex items-center space-x-2 group cursor-pointer">
          <div
            class="w-10 h-10 bg-gradient-to-br from-yellow-400 to-yellow-500 rounded-lg flex items-center justify-center group-hover:scale-110 transition-transform duration-500"
          >
            <Atom
              class="w-6 h-6 animate-spin-slow transition-colors duration-300"
              :style="{ color: isDark ? '#facc15' : '#166534' }"
            />
          </div>
          <span
            class="text-2xl font-bold text-green-800 dark:text-yellow-400"
            :style="{ color: isDark ? '#facc15' : '#166534' }"
          >
            ThinkSci
          </span>
        </div>

        <!-- Navigation Links -->
        <div class="hidden md:flex items-center space-x-16">
          <a
            v-for="link in navigationLinks"
            :key="link.href"
            :href="link.href"
            @click="smoothScroll"
            class="relative font-medium group transition-colors duration-300 nav-link"
            :style="{
              color: isDark ? '#d1d5db' : '#374151',
              '--hover-color': isDark ? '#facc15' : '#059669',
            }"
            @mouseenter="
              $event.target.style.color = isDark ? '#facc15' : '#059669'
            "
            @mouseleave="
              $event.target.style.color = isDark ? '#d1d5db' : '#374151'
            "
          >
            {{ link.text }}
            <span
              class="absolute -bottom-1 left-0 w-0 h-0.5 bg-gradient-to-r from-yellow-400 to-green-500 group-hover:w-full transition-all duration-500"
            ></span>
          </a>
        </div>

        <!-- Theme Toggle -->
        <div class="flex items-center space-x-4">
          <button
            @click="$emit('toggle-theme')"
            class="p-2 rounded-xl bg-gradient-to-r from-yellow-100 to-green-100 dark:from-gray-800 dark:to-gray-700 transition-all duration-500 text-gray-700 dark:text-gray-300 hover:scale-110 hover:shadow-lg group"
            aria-label="Toggle theme"
          >
            <Sun
              v-if="isDark"
              class="w-5 h-5 group-hover:rotate-180 transition-transform duration-800"
            />
            <Moon
              v-else
              class="w-5 h-5 group-hover:-rotate-12 transition-transform duration-800"
            />
          </button>

          <!-- Mobile Menu Button -->
          <button
            @click="$emit('toggle-mobile-menu')"
            class="md:hidden p-2 rounded-xl bg-gradient-to-r from-yellow-100 to-green-100 dark:from-gray-800 dark:to-gray-700 transition-all duration-500 hover:scale-110 hover:shadow-lg"
            aria-label="Toggle mobile menu"
          >
            <div class="relative w-5 h-5">
              <span
                class="absolute block w-5 h-0.5 bg-gray-600 dark:bg-gray-300 transition-all duration-500"
                :class="showMobileMenu ? 'top-2 rotate-45' : 'top-1'"
              ></span>
              <span
                class="absolute block w-5 h-0.5 bg-gray-600 dark:bg-gray-300 transition-all duration-500 top-2"
                :class="showMobileMenu ? 'opacity-0' : 'opacity-100'"
              ></span>
              <span
                class="absolute block w-5 h-0.5 bg-gray-600 dark:bg-gray-300 transition-all duration-500"
                :class="showMobileMenu ? 'top-2 -rotate-45' : 'top-3'"
              ></span>
            </div>
          </button>
        </div>
      </div>

      <!-- Mobile Menu -->
      <Transition
        enter-active-class="transition-all duration-300 ease-out"
        leave-active-class="transition-all duration-300 ease-in"
        enter-from-class="opacity-0 -translate-y-4 scale-95"
        enter-to-class="opacity-100 translate-y-0 scale-100"
        leave-from-class="opacity-100 translate-y-0 scale-100"
        leave-to-class="opacity-0 -translate-y-4 scale-95"
      >
        <div
          v-if="showMobileMenu"
          class="md:hidden absolute top-full left-0 right-0 bg-white/95 dark:bg-gray-900/95 backdrop-blur-xl border-b border-gray-200 dark:border-gray-700 shadow-2xl"
        >
          <div class="px-4 py-6 divide-y divide-gray-200 dark:divide-gray-700">
            <a
              v-for="link in navigationLinks"
              :key="link.href"
              :href="link.href"
              @click="$emit('close-mobile-menu')"
              class="block px-6 py-4 text-lg font-medium text-gray-700 dark:text-gray-300 hover:text-yellow-500 dark:hover:text-yellow-400 transition-all duration-300 relative"
            >
              {{ link.text }}
              <span
                class="absolute bottom-0 left-0 w-0 h-0.5 bg-gradient-to-r from-yellow-400 to-green-500 transition-all duration-500 group-hover:w-full"
              ></span>
            </a>
          </div>
        </div>
      </Transition>
    </div>
  </nav>
</template>

<script setup>
import { Atom, Sun, Moon } from "lucide-vue-next";

// Props
defineProps({
  isDark: Boolean,
  showMobileMenu: Boolean,
});

// Emits
defineEmits(["toggle-theme", "toggle-mobile-menu", "close-mobile-menu"]);

// Data
const navigationLinks = [
  { href: "#hero", text: "Home" },
  { href: "#about", text: "About" },
  { href: "#developers", text: "Team" },
];

// Methods
const smoothScroll = (event) => {
  event.preventDefault();
  const target = event.target.getAttribute("href");
  const element = document.querySelector(target);
  if (element) {
    element.scrollIntoView({ behavior: "smooth" });
  }
};
</script>
