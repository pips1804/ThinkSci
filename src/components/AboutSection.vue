<template>
  <section
    id="about"
    class="py-20 px-4 bg-white dark:bg-gray-900 transition-colors duration-300 relative overflow-hidden"
  >
    <!-- Background Pattern -->
    <div class="absolute inset-0 opacity-5 dark:opacity-10">
      <div
        class="absolute inset-0"
        style="
          background-image: radial-gradient(
            circle at 2px 2px,
            currentColor 1px,
            transparent 0
          );
          background-size: 40px 40px;
        "
      ></div>
    </div>

    <div class="max-w-7xl mx-auto relative z-10">
      <div class="text-center mb-20">
        <h2
          class="text-4xl md:text-5xl lg:text-6xl font-bold text-[#116530] dark:text-yellow-400 mb-6"
        >
          Why Choose
          <span class="relative inline-block">
            <span class="relative z-10 text-[#116530] dark:text-white"
              >ThinkSci?</span
            >
            <span
              class="absolute inset-0 bg-gradient-to-r from-yellow-400/30 to-green-400/30 rounded-lg blur-lg transform scale-110"
            ></span>
          </span>
        </h2>
        <p
          class="text-xl lg:text-2xl text-gray-600 dark:text-gray-300 max-w-4xl mx-auto leading-relaxed"
        >
          We make science learning fun, interactive, and engaging for Grade 7
          students with cutting-edge technology and proven educational methods.
        </p>
      </div>

      <!-- Enhanced Features Grid with Morphing Icons -->
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="(feature, index) in features"
          :key="index"
          class="group bg-gradient-to-br from-white to-gray-50 dark:from-gray-800 dark:to-gray-900 rounded-3xl p-8 text-center shadow-lg hover:shadow-2xl transition-all duration-600 transform hover:-translate-y-4 hover:scale-105 border border-gray-100 dark:border-gray-700 relative overflow-hidden"
        >
          <!-- Background Glow -->
          <div
            class="absolute inset-0 bg-gradient-to-br from-yellow-400/5 to-green-400/5 opacity-0 group-hover:opacity-100 transition-opacity duration-600"
          ></div>

          <!-- Floating Particles for Features -->
          <div
            class="absolute inset-0 opacity-0 group-hover:opacity-60 transition-opacity duration-500"
          >
            <div
              v-for="n in 8"
              :key="n"
              class="absolute w-1 h-1 bg-gradient-to-r from-yellow-400 to-green-400 rounded-full animate-ping"
              :style="{
                left: Math.random() * 100 + '%',
                top: Math.random() * 100 + '%',
                animationDelay: n * 150 + 'ms',
              }"
            ></div>
          </div>

          <div class="relative z-10">
            <div
              class="w-20 h-20 rounded-2xl flex items-center justify-center mx-auto mb-6 shadow-lg group-hover:scale-110 group-hover:rotate-3 transition-all duration-600 relative overflow-hidden"
              :class="feature.iconBg"
            >
              <!-- Icon with morphing effects -->
              <component
                :is="feature.icon"
                class="w-10 h-10 transition-all duration-500 z-10 relative"
                :class="[feature.iconColor, feature.morphEffect]"
              />

              <!-- Ripple effect on hover -->
              <div
                class="absolute inset-0 rounded-2xl bg-white/20 scale-0 group-hover:scale-100 opacity-0 group-hover:opacity-100 transition-all duration-500"
              ></div>
            </div>

            <h3
              class="text-2xl lg:text-3xl font-bold text-[#116530] dark:text-yellow-400 mb-4 group-hover:text-yellow-600 dark:group-hover:text-white transition-colors duration-500"
            >
              {{ feature.title }}
            </h3>

            <p class="text-gray-600 dark:text-gray-300 leading-relaxed text-lg">
              {{ feature.description }}
            </p>

            <!-- Progress indicator -->
            <div
              class="mt-6 w-full bg-gray-200 dark:bg-gray-700 rounded-full h-1 opacity-0 group-hover:opacity-100 transition-opacity duration-500"
            >
              <div
                class="bg-gradient-to-r from-yellow-400 to-green-500 h-1 rounded-full transition-all duration-1000 ease-out"
                :style="{ width: '0%' }"
                :class="'group-hover:w-full'"
              ></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import {
  BookOpen,
  Target,
  Trophy,
  Users,
  BarChart,
  Shield,
} from "lucide-vue-next";

// Enhanced features with morphing effects
const features = [
  {
    icon: BookOpen,
    iconBg: "bg-gradient-to-br from-[#FFCC1D] to-yellow-400",
    iconColor: "text-[#116530]",
    title: "Interactive Science Lessons",
    description:
      "Learn science through animations, simulations, and experiments.",
  },
  {
    icon: Target,
    iconBg: "bg-gradient-to-br from-[#116530] to-green-600",
    iconColor: "text-[#FFCC1D]",
    title: "Adaptive Learning Paths",
    description:
      "Content adjusts to each student’s pace for better understanding.",
  },
  {
    icon: Trophy,
    iconBg: "bg-gradient-to-br from-[#FFCC1D] to-yellow-400",
    iconColor: "text-[#116530]",
    title: "Gamified Challenges",
    description:
      "Earn badges and rewards that make learning fun and motivating.",
  },
  {
    icon: Users,
    iconBg: "bg-gradient-to-br from-[#116530] to-green-600",
    iconColor: "text-[#FFCC1D]",
    title: "Peer Collaboration",
    description: "Work with classmates on group tasks and shared discoveries.",
  },
  {
    icon: BarChart,
    iconBg: "bg-gradient-to-br from-[#FFCC1D] to-yellow-400",
    iconColor: "text-[#116530]",
    title: "Progress Monitoring",
    description: "Track learning milestones with clear reports and feedback.",
  },
  {
    icon: Shield,
    iconBg: "bg-gradient-to-br from-[#116530] to-green-600",
    iconColor: "text-[#FFCC1D]",
    title: "Safe & Child-Friendly",
    description:
      "Secure platform with privacy protection and parental controls.",
  },
];
</script>
