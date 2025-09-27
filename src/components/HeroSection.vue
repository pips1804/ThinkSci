<template>
  <section
    id="hero"
    class="relative bg-gradient-to-br from-[#E8E8CC] via-[#FFCC1D] to-[#E8E8CC] dark:from-gray-900 dark:via-gray-800 dark:to-gray-900 min-h-screen flex items-center px-4 py-12 sm:py-20 lg:py-24 overflow-hidden"
  >
    <!-- Enhanced Background Elements with Floating Particles -->
    <div class="absolute inset-0 overflow-hidden pointer-events-none">
      <!-- Original floating blobs -->
      <div
        class="absolute top-20 left-10 w-32 h-32 bg-gradient-to-r from-yellow-400/20 to-green-400/20 rounded-full blur-xl animate-float"
      ></div>
      <div
        class="absolute bottom-20 right-10 w-48 h-48 bg-gradient-to-r from-green-400/20 to-yellow-400/20 rounded-full blur-xl animate-float-delayed"
      ></div>

      <!-- Floating Particles/Atoms -->
      <div
        v-for="particle in floatingParticles"
        :key="particle.id"
        class="absolute rounded-full animate-float-random opacity-60"
        :class="particle.class"
        :style="{
          left: particle.left + '%',
          top: particle.top + '%',
          animationDelay: particle.delay + 's',
          animationDuration: particle.duration + 's',
        }"
      >
        <component
          :is="particle.icon"
          v-if="particle.icon"
          class="w-full h-full text-current"
        />
      </div>
    </div>

    <div class="max-w-7xl mx-auto relative z-10 w-full">
      <div class="grid lg:grid-cols-2 gap-8 lg:gap-20 xl:gap-24 items-center">
        <!-- Hero Content -->
        <div
          class="text-center lg:text-left space-y-4 sm:space-y-6 lg:space-y-8 order-2 lg:order-1"
        >
          <div class="space-y-4 sm:space-y-6">
            <h1
              class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-bold leading-tight"
            >
              <span
                class="block text-[#116530] dark:text-yellow-400 mb-1 sm:mb-2 animate-fade-in-up"
              >
                Learn Science
              </span>
              <!-- <span
                class="block text-[#116530] dark:text-yellow-400 mb-1 sm:mb-2 animate-fade-in-up animation-delay-200"
              >
                with
              </span> -->
              <span
                class="block text-[#116530] dark:text-white animate-fade-in-up animation-delay-400 relative"
              >
                <span class="relative z-10"> with ThinkSci!</span>
                <span
                  class="absolute inset-0 bg-gradient-to-r from-yellow-400/20 to-green-400/20 rounded-lg blur-xl transform scale-110"
                ></span>
              </span>
            </h1>

            <p
              class="text-lg sm:text-xl lg:text-2xl text-gray-700 dark:text-gray-300 leading-relaxed max-w-2xl mx-auto lg:mx-0 animate-fade-in-up animation-delay-600"
            >
              Unlock the secrets of Force, Motion & Energy! Progress through
              video lessons, earn badges, and nurture your virtual pet in this
              offline Grade 7 physics adventure.
            </p>
          </div>

          <!-- Download Buttons -->
          <div
            class="flex flex-col sm:flex-row gap-4 sm:gap-6 justify-center lg:justify-start animate-fade-in-up animation-delay-800"
          >
            <!-- Download for Android -->
            <a
              href="https://www.mediafire.com/file/4lwo5eelp6b071c/ThinkSci.apk/file"
              target="_blank"
              rel="noopener noreferrer"
              class="group bg-[#116530] hover:bg-green-600 text-white px-6 sm:px-8 py-3 sm:py-4 rounded-2xl font-semibold text-base sm:text-lg flex items-center justify-center space-x-2 sm:space-x-3 transition-all duration-600 ease-out transform hover:scale-105 hover:-translate-y-1 shadow-2xl hover:shadow-3xl"
            >
              <Smartphone
                class="w-5 h-5 sm:w-6 sm:h-6 group-hover:animate-bounce transition-transform duration-500"
              />
              <span>Download for Android</span>
              <ArrowRight
                class="w-4 h-4 sm:w-5 sm:h-5 group-hover:translate-x-1 transition-transform duration-600 ease-out"
              />
            </a>

            <!-- Watch Demo -->
            <a
              href="https://www.mediafire.com/file/4lwo5eelp6b071c/ThinkSci.apk/file"
              target="_blank"
              rel="noopener noreferrer"
              class="group bg-white/90 dark:bg-gray-800/90 backdrop-blur-sm text-[#116530] dark:text-yellow-400 border-2 border-[#116530] dark:border-yellow-400 px-6 sm:px-8 py-3 sm:py-4 rounded-2xl font-semibold text-base sm:text-lg flex items-center justify-center space-x-2 sm:space-x-3 transition-all duration-600 ease-out transform hover:scale-105 hover:-translate-y-1 shadow-2xl hover:shadow-3xl hover:bg-white dark:hover:bg-gray-800"
            >
              <Play
                class="w-5 h-5 sm:w-6 sm:h-6 group-hover:scale-110 transition-transform duration-600 ease-out"
              />
              <span>Watch Demo</span>
            </a>
          </div>

          <!-- Stats -->
          <div
            class="grid grid-cols-3 gap-4 sm:gap-6 lg:gap-8 mt-12 sm:mt-16 animate-fade-in-up animation-delay-1000"
          >
            <div
              v-for="(stat, index) in stats"
              :key="index"
              class="text-center group"
            >
              <div
                class="text-2xl sm:text-3xl lg:text-4xl xl:text-5xl font-bold text-[#116530] dark:text-yellow-400 mb-1 sm:mb-2 group-hover:scale-105 transition-transform duration-600 ease-out"
              >
                {{ stat.value }}
              </div>
              <div
                class="text-xs sm:text-sm lg:text-base text-green-800 dark:text-gray-400 font-medium"
              >
                {{ stat.label }}
              </div>
            </div>
          </div>
        </div>

        <!-- Hero Visual -->
        <div
          class="relative animate-fade-in-right animation-delay-400 order-1 lg:order-2 mb-8 lg:mb-0"
        >
          <!-- Container with max width and centered alignment for smaller screens -->
          <div class="max-w-sm sm:max-w-md lg:max-w-none mx-auto">
            <div
              class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-xl rounded-3xl p-4 sm:p-6 lg:p-8 shadow-2xl transform rotate-1 sm:rotate-2 lg:rotate-3 hover:rotate-0 transition-all duration-800 ease-out hover:scale-105 border border-white/20 dark:border-gray-700/20"
            >
              <div class="grid grid-cols-2 gap-3 sm:gap-4 lg:gap-6">
                <!-- Science Icons -->
                <div
                  v-for="(icon, index) in scienceIcons"
                  :key="index"
                  class="aspect-square rounded-xl sm:rounded-2xl p-3 sm:p-4 lg:p-6 flex items-center justify-center transition-all duration-600 ease-out hover:scale-105 hover:-translate-y-2 shadow-lg hover:shadow-xl"
                  :class="icon.bgClass"
                  :style="{ animationDelay: `${index * 200}ms` }"
                >
                  <component
                    :is="icon.component"
                    class="w-6 h-6 sm:w-8 sm:h-8 lg:w-10 lg:h-10 xl:w-12 xl:h-12"
                    :class="icon.iconClass"
                  />
                </div>
              </div>

              <!-- Floating Elements - Smaller on mobile -->
              <div
                class="absolute -top-3 -right-3 sm:-top-4 sm:-right-4 bg-[#FFCC1D] rounded-full p-1.5 sm:p-2 lg:p-3 animate-float shadow-lg"
              >
                <Star
                  class="w-3 h-3 sm:w-4 sm:h-4 lg:w-6 lg:h-6 text-[#116530]"
                />
              </div>
              <div
                class="absolute -bottom-3 -left-3 sm:-bottom-4 sm:-left-4 bg-[#116530] rounded-full p-1.5 sm:p-2 lg:p-3 animate-float-delayed shadow-lg"
              >
                <Lightbulb
                  class="w-3 h-3 sm:w-4 sm:h-4 lg:w-6 lg:h-6 text-[#FFCC1D]"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import {
  Smartphone,
  Play,
  ArrowRight,
  Star,
  Lightbulb,
  Atom,
  Microscope,
  Beaker,
  Zap,
  Sparkles,
  Circle,
} from "lucide-vue-next";

// Generate floating particles data
const generateFloatingParticles = () => {
  const particles = [];
  const icons = [Atom, Sparkles, Circle, Star];
  const colors = [
    "text-yellow-400/40",
    "text-green-400/40",
    "text-blue-400/40",
    "text-purple-400/40",
    "text-pink-400/40",
  ];
  const sizes = ["w-2 h-2", "w-3 h-3", "w-4 h-4", "w-1 h-1"];

  for (let i = 0; i < 25; i++) {
    particles.push({
      id: i,
      left: Math.random() * 100,
      top: Math.random() * 100,
      delay: Math.random() * 5,
      duration: 3 + Math.random() * 4,
      class: `${sizes[Math.floor(Math.random() * sizes.length)]} ${
        colors[Math.floor(Math.random() * colors.length)]
      }`,
      icon:
        Math.random() > 0.3
          ? icons[Math.floor(Math.random() * icons.length)]
          : null,
    });
  }
  return particles;
};

// Data
const floatingParticles = generateFloatingParticles();

const stats = [
  { value: "14", label: "Video Lessons" },
  { value: "100+", label: "Downloads" },
  { value: "70%", label: "Development Progress" },
];

const scienceIcons = [
  {
    component: Atom,
    bgClass: "bg-gradient-to-br from-[#FFCC1D] to-yellow-400",
    iconClass: "text-[#116530] group-hover:animate-spin",
    hoverEffect: "group-hover:drop-shadow-lg group-hover:brightness-110",
  },
  {
    component: Microscope,
    bgClass: "bg-gradient-to-br from-[#116530] to-green-600",
    iconClass: "text-white group-hover:scale-110",
    hoverEffect: "group-hover:drop-shadow-lg group-hover:brightness-110",
  },
  {
    component: Beaker,
    bgClass: "bg-gradient-to-br from-[#E8E8CC] to-gray-200",
    iconClass: "text-[#116530] group-hover:animate-bounce",
    hoverEffect: "group-hover:drop-shadow-lg group-hover:brightness-110",
  },
  {
    component: Zap,
    bgClass: "bg-gradient-to-br from-[#FFCC1D] via-yellow-400 to-[#116530]",
    iconClass: "text-white group-hover:animate-pulse",
    hoverEffect: "group-hover:drop-shadow-lg group-hover:brightness-110",
  },
];
</script>
