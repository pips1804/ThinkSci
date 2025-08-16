<template>
  <div
    :class="{ dark: isDark }"
    class="min-h-screen transition-colors duration-300"
  >
    <!-- Navigation -->
    <nav
      class="bg-white/80 dark:bg-gray-900/80 backdrop-blur-xl shadow-lg sticky top-0 z-50 transition-all duration-300 border-b border-white/20 dark:border-gray-700/20"
    >
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between items-center h-16">
          <!-- Logo -->
          <div class="flex items-center space-x-2 group cursor-pointer">
            <div
              class="w-10 h-10 bg-gradient-to-br from-yellow-400 to-yellow-500 rounded-lg flex items-center justify-center group-hover:scale-110 transition-transform duration-500 shadow-lg"
            >
              <Atom class="w-6 h-6 text-green-800 animate-spin-slow" />
            </div>
            <span class="text-2xl font-bold text-green-800 dark:text-yellow-400"
              >ThinkSci</span
            >
          </div>

          <!-- Navigation Links -->
          <div class="hidden md:flex items-center space-x-8">
            <a
              v-for="link in navigationLinks"
              :key="link.href"
              :href="link.href"
              @click="smoothScroll"
              class="relative text-gray-700 dark:text-gray-300 hover:text-yellow-500 dark:hover:text-yellow-400 transition-all duration-400 font-medium group"
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
              @click="toggleTheme"
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
              @click="toggleMobileMenu"
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

        <!-- Enhanced Mobile Menu -->
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
            <div class="px-4 py-6 space-y-4">
              <a
                v-for="(link, index) in navigationLinks"
                :key="link.href"
                :href="link.href"
                @click="closeMobileMenu"
                class="block px-6 py-4 text-lg font-medium text-gray-700 dark:text-gray-300 hover:text-yellow-500 dark:hover:text-yellow-400 hover:bg-gradient-to-r hover:from-yellow-50 hover:to-green-50 dark:hover:from-gray-800 dark:hover:to-gray-700 rounded-xl transition-all duration-500 transform hover:scale-102 hover:shadow-lg"
                :style="{ animationDelay: `${index * 50}ms` }"
              >
                {{ link.text }}
              </a>

              <!-- Mobile Theme Toggle -->
              <button
                @click="toggleTheme"
                class="flex items-center space-x-3 px-6 py-4 w-full text-left text-lg font-medium text-gray-700 dark:text-gray-300 hover:text-yellow-500 dark:hover:text-yellow-400 hover:bg-gradient-to-r hover:from-yellow-50 hover:to-green-50 dark:hover:from-gray-800 dark:hover:to-gray-700 rounded-xl transition-all duration-500"
              >
                <Sun v-if="isDark" class="w-6 h-6" />
                <Moon v-else class="w-6 h-6" />
                <span>{{ isDark ? "Light Mode" : "Dark Mode" }}</span>
              </button>
            </div>
          </div>
        </Transition>
      </div>
    </nav>

    <!-- Hero Section -->
    <section
      id="hero"
      class="relative bg-gradient-to-br from-[#E8E8CC] via-[#FFCC1D] to-[#E8E8CC] dark:from-gray-900 dark:via-gray-800 dark:to-gray-900 min-h-screen flex items-center px-4 py-20 sm:py-24 overflow-hidden"
    >
      <!-- Background Elements -->
      <div class="absolute inset-0 overflow-hidden pointer-events-none">
        <div
          class="absolute top-20 left-10 w-32 h-32 bg-gradient-to-r from-yellow-400/20 to-green-400/20 rounded-full blur-xl animate-float"
        ></div>
        <div
          class="absolute bottom-20 right-10 w-48 h-48 bg-gradient-to-r from-green-400/20 to-yellow-400/20 rounded-full blur-xl animate-float-delayed"
        ></div>
      </div>

      <div class="max-w-7xl mx-auto relative z-10 w-full">
        <div class="grid lg:grid-cols-2 gap-8 lg:gap-12 items-center">
          <!-- Hero Content -->
          <div
            class="text-center lg:text-left space-y-6 sm:space-y-8 order-2 lg:order-1"
          >
            <div class="space-y-4 sm:space-y-6">
              <h1
                class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-bold leading-tight"
              >
                <span
                  class="block text-[#116530] dark:text-yellow-400 mb-1 sm:mb-2 animate-fade-in-up"
                >
                  Discover Science
                </span>
                <span
                  class="block text-[#116530] dark:text-yellow-400 mb-1 sm:mb-2 animate-fade-in-up animation-delay-200"
                >
                  with
                </span>
                <span
                  class="block text-[#116530] dark:text-white animate-fade-in-up animation-delay-400 relative"
                >
                  <span class="relative z-10">ThinkSci!</span>
                  <span
                    class="absolute inset-0 bg-gradient-to-r from-yellow-400/20 to-green-400/20 rounded-lg blur-xl transform scale-110"
                  ></span>
                </span>
              </h1>

              <p
                class="text-lg sm:text-xl lg:text-2xl text-gray-700 dark:text-gray-300 leading-relaxed max-w-2xl mx-auto lg:mx-0 animate-fade-in-up animation-delay-600"
              >
                The ultimate science learning adventure for Grade 7 students!
                Explore, experiment, and excel with interactive lessons, fun
                quizzes, and amazing discoveries.
              </p>
            </div>

            <!-- Enhanced Download Buttons -->
            <div
              class="flex flex-col sm:flex-row gap-4 sm:gap-6 justify-center lg:justify-start animate-fade-in-up animation-delay-800"
            >
              <button
                class="group bg-[#116530] hover:bg-green-600 text-white px-6 sm:px-8 py-3 sm:py-4 rounded-2xl font-semibold text-base sm:text-lg flex items-center justify-center space-x-2 sm:space-x-3 transition-all duration-600 ease-out transform hover:scale-105 hover:-translate-y-1 shadow-2xl hover:shadow-3xl"
              >
                <Smartphone
                  class="w-5 h-5 sm:w-6 sm:h-6 group-hover:animate-bounce transition-transform duration-500"
                />
                <span>Download for Android</span>
                <ArrowRight
                  class="w-4 h-4 sm:w-5 sm:h-5 group-hover:translate-x-1 transition-transform duration-600 ease-out"
                />
              </button>

              <button
                class="group bg-white/90 dark:bg-gray-800/90 backdrop-blur-sm text-[#116530] dark:text-yellow-400 border-2 border-[#116530] dark:border-yellow-400 px-6 sm:px-8 py-3 sm:py-4 rounded-2xl font-semibold text-base sm:text-lg flex items-center justify-center space-x-2 sm:space-x-3 transition-all duration-600 ease-out transform hover:scale-105 hover:-translate-y-1 shadow-2xl hover:shadow-3xl hover:bg-white dark:hover:bg-gray-800"
              >
                <Play
                  class="w-5 h-5 sm:w-6 sm:h-6 group-hover:scale-110 transition-transform duration-600 ease-out"
                />
                <span>Watch Demo</span>
              </button>
            </div>

            <!-- Enhanced Stats -->
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
                  class="text-xs sm:text-sm lg:text-base text-gray-600 dark:text-gray-400 font-medium"
                >
                  {{ stat.label }}
                </div>
              </div>
            </div>
          </div>

          <!-- Enhanced Hero Visual -->
          <div
            class="relative animate-fade-in-right animation-delay-400 order-1 lg:order-2 mb-8 lg:mb-0"
          >
            <div
              class="bg-white/80 dark:bg-gray-800/80 backdrop-blur-xl rounded-3xl p-6 sm:p-8 shadow-2xl transform rotate-3 hover:rotate-0 transition-all duration-800 ease-out hover:scale-105 border border-white/20 dark:border-gray-700/20"
            >
              <div class="grid grid-cols-2 gap-4 sm:gap-6">
                <!-- Enhanced Science Icons -->
                <div
                  v-for="(icon, index) in scienceIcons"
                  :key="index"
                  class="aspect-square rounded-2xl p-4 sm:p-6 flex items-center justify-center transition-all duration-600 ease-out hover:scale-105 hover:-translate-y-2 shadow-lg hover:shadow-xl"
                  :class="icon.bgClass"
                  :style="{ animationDelay: `${index * 200}ms` }"
                >
                  <component
                    :is="icon.component"
                    class="w-8 h-8 sm:w-10 sm:h-10 lg:w-12 lg:h-12"
                    :class="icon.iconClass"
                  />
                </div>
              </div>

              <!-- Enhanced Floating Elements -->
              <div
                class="absolute -top-4 -right-4 bg-[#FFCC1D] rounded-full p-2 sm:p-3 animate-float shadow-lg"
              >
                <Star class="w-4 h-4 sm:w-6 sm:h-6 text-[#116530]" />
              </div>
              <div
                class="absolute -bottom-4 -left-4 bg-[#116530] rounded-full p-2 sm:p-3 animate-float-delayed shadow-lg"
              >
                <Lightbulb class="w-4 h-4 sm:w-6 sm:h-6 text-[#FFCC1D]" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
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
            students with cutting-edge technology and proven educational
            methods.
          </p>
        </div>

        <!-- Enhanced Features Grid -->
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

            <div class="relative z-10">
              <div
                class="w-20 h-20 rounded-2xl flex items-center justify-center mx-auto mb-6 shadow-lg group-hover:scale-110 group-hover:rotate-3 transition-all duration-600"
                :class="feature.iconBg"
              >
                <component
                  :is="feature.icon"
                  class="w-10 h-10"
                  :class="feature.iconColor"
                />
              </div>

              <h3
                class="text-2xl lg:text-3xl font-bold text-[#116530] dark:text-yellow-400 mb-4 group-hover:text-yellow-600 dark:group-hover:text-white transition-colors duration-500"
              >
                {{ feature.title }}
              </h3>

              <p
                class="text-gray-600 dark:text-gray-300 leading-relaxed text-lg"
              >
                {{ feature.description }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Enhanced Developers Section -->
    <section
      id="developers"
      class="py-20 px-4 bg-gradient-to-br from-[#E8E8CC] via-white to-[#E8E8CC] dark:from-gray-800 dark:via-gray-900 dark:to-gray-800 transition-colors duration-300 relative"
    >
      <div class="max-w-8xl mx-auto">
        <div class="text-center mb-20">
          <h2
            class="text-4xl md:text-5xl lg:text-6xl font-bold text-[#116530] dark:text-yellow-400 mb-6"
          >
            Meet Our
            <span class="relative inline-block">
              <span class="relative z-10 text-[#116530] dark:text-white"
                >Amazing Team</span
              >
              <span
                class="absolute inset-0 bg-gradient-to-r from-yellow-400/30 to-green-400/30 rounded-lg blur-lg transform scale-110"
              ></span>
            </span>
          </h2>
          <p
            class="text-xl lg:text-2xl text-gray-600 dark:text-gray-300 max-w-4xl mx-auto leading-relaxed"
          >
            Passionate educators and developers working together to
            revolutionize science education for the next generation.
          </p>
        </div>

        <!-- Enhanced Team Grid -->
        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8 lg:mx-10">
          <div
            v-for="(member, index) in teamMembers"
            :key="index"
            class="group bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm rounded-3xl p-8 text-center shadow-lg hover:shadow-2xl transition-all duration-700 transform hover:-translate-y-6 hover:scale-105 border border-white/20 dark:border-gray-700/20 relative overflow-hidden"
          >
            <!-- Background Glow -->
            <div
              class="absolute inset-0 bg-gradient-to-br from-yellow-400/10 to-green-400/10 opacity-0 group-hover:opacity-100 transition-opacity duration-700"
            ></div>

            <div class="relative z-10">
              <div
                class="w-28 h-28 rounded-full flex items-center justify-center mx-auto mb-6 shadow-xl group-hover:scale-110 group-hover:rotate-6 transition-all duration-700"
                :class="member.avatarBg"
              >
                <User class="w-14 h-14 text-white" />
              </div>

              <h3
                class="text-xl lg:text-2xl font-bold text-[#116530] dark:text-yellow-400 mb-2 group-hover:text-yellow-600 dark:group-hover:text-white transition-colors duration-500"
              >
                {{ member.name }}
              </h3>

              <p
                class="text-[#FFCC1D] dark:text-yellow-300 font-semibold mb-4 text-lg"
              >
                {{ member.role }}
              </p>

              <p class="text-gray-600 dark:text-gray-300 mb-6 leading-relaxed">
                {{ member.description }}
              </p>

              <div class="flex justify-center space-x-4">
                <button
                  v-for="social in member.socials"
                  :key="social.name"
                  class="p-3 bg-gray-100 dark:bg-gray-700 rounded-xl hover:bg-[#FFCC1D] hover:scale-110 hover:-translate-y-1 transition-all duration-500 shadow-md hover:shadow-lg"
                  :aria-label="social.name"
                >
                  <component
                    :is="social.icon"
                    class="w-5 h-5 text-[#116530] dark:text-gray-300 hover:text-white transition-colors duration-500"
                  />
                </button>
              </div>
            </div>
          </div>
        </div>

        <!-- Enhanced Call to Action -->
        <div class="text-center mt-20">
          <div
            class="bg-white/90 dark:bg-gray-800/90 backdrop-blur-xl rounded-3xl p-12 shadow-2xl max-w-4xl mx-auto border border-white/20 dark:border-gray-700/20 relative overflow-hidden"
          >
            <!-- Background Elements -->
            <div
              class="absolute top-0 left-0 w-32 h-32 bg-gradient-to-r from-yellow-400/20 to-green-400/20 rounded-full blur-2xl"
            ></div>
            <div
              class="absolute bottom-0 right-0 w-40 h-40 bg-gradient-to-r from-green-400/20 to-yellow-400/20 rounded-full blur-2xl"
            ></div>

            <div class="relative z-10">
              <h3
                class="text-3xl lg:text-4xl font-bold text-[#116530] dark:text-yellow-400 mb-6"
              >
                Ready to Join the Science Adventure?
              </h3>
              <p
                class="text-xl lg:text-2xl text-gray-600 dark:text-gray-300 mb-10 leading-relaxed"
              >
                Download ThinkSci today and start your exciting journey into the
                world of science!
              </p>
              <button
                class="group bg-[#116530] hover:bg-green-600 text-white px-12 py-5 rounded-2xl font-bold text-xl transition-all duration-600 transform hover:scale-110 hover:-translate-y-2 shadow-2xl hover:shadow-3xl relative overflow-hidden"
              >
                <span
                  class="relative z-10 flex items-center justify-center space-x-3"
                >
                  <span>Get Started Now!</span>
                  <Rocket
                    class="w-6 h-6 group-hover:translate-x-1 group-hover:-translate-y-1 transition-transform duration-500"
                  />
                </span>
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Enhanced Footer -->
    <footer
      class="bg-[#116530] dark:from-gray-900 dark:via-gray-800 dark:to-gray-900 text-white py-16 px-4 transition-colors duration-300 relative overflow-hidden"
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
          <!-- Enhanced Logo and Description -->
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
              Making science education fun, interactive, and accessible for
              Grade 7 students worldwide. Join thousands of young scientists on
              their learning journey!
            </p>
            <div class="flex space-x-4">
              <button
                v-for="social in footerSocials"
                :key="social.name"
                class="p-3 bg-[#FFCC1D] rounded-xl hover:bg-yellow-300 transition-all duration-500 hover:scale-110 hover:-translate-y-1 shadow-lg hover:shadow-xl"
                :aria-label="social.name"
              >
                <component :is="social.icon" class="w-6 h-6 text-[#116530]" />
              </button>
            </div>
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

          <!-- Contact -->
          <div>
            <h4 class="text-[#FFCC1D] font-bold text-xl mb-6">Contact Us</h4>
            <ul class="space-y-4">
              <li
                v-for="contact in contactInfo"
                :key="contact.type"
                class="flex items-center space-x-3 group"
              >
                <component
                  :is="contact.icon"
                  class="w-5 h-5 text-[#FFCC1D] group-hover:scale-110 transition-transform duration-500"
                />
                <span class="text-gray-300 text-lg">{{ contact.value }}</span>
              </li>
            </ul>
          </div>
        </div>

        <div class="border-t border-gray-600/30 mt-12 pt-8 text-center">
          <p class="text-gray-300 text-lg">
            © 2024 ThinkSci. All rights reserved.
          </p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from "vue";
import {
  Atom,
  Sun,
  Moon,
  Smartphone,
  Play,
  BookOpen,
  Target,
  Trophy,
  Users,
  BarChart,
  Shield,
  User,
  Mail,
  Linkedin,
  Github,
  Dribbble,
  Star,
  Lightbulb,
  Microscope,
  Beaker,
  Zap,
  Facebook,
  Twitter,
  Instagram,
  Phone,
  MapPin,
  ArrowRight,
  Sparkles,
  Rocket,
} from "lucide-vue-next";

// Reactive state
const isDark = ref(true);
const showMobileMenu = ref(false);

// Computed data
const navigationLinks = [
  { href: "#hero", text: "Home" },
  { href: "#about", text: "About" },
  { href: "#developers", text: "Team" },
];

const stats = [
  { value: "50+", label: "Interactive Lessons" },
  { value: "1000+", label: "Happy Students" },
  { value: "95%", label: "Success Rate" },
];

const scienceIcons = [
  {
    component: Atom,
    bgClass: "bg-gradient-to-br from-[#FFCC1D] to-yellow-400",
    iconClass: "text-[#116530]",
  },
  {
    component: Microscope,
    bgClass: "bg-gradient-to-br from-[#116530] to-green-600",
    iconClass: "text-white",
  },
  {
    component: Beaker,
    bgClass: "bg-gradient-to-br from-[#E8E8CC] to-gray-200",
    iconClass: "text-[#116530]",
  },
  {
    component: Zap,
    bgClass: "bg-gradient-to-br from-[#FFCC1D] via-yellow-400 to-[#116530]",
    iconClass: "text-white",
  },
];

const features = [
  {
    icon: BookOpen,
    iconBg: "bg-gradient-to-br from-[#FFCC1D] to-yellow-400",
    iconColor: "text-[#116530]",
    title: "Interactive Lessons",
    description:
      "Engaging multimedia lessons with animations, videos, and interactive experiments that make complex concepts easy to understand.",
  },
  {
    icon: Target,
    iconBg: "bg-gradient-to-br from-[#116530] to-green-600",
    iconColor: "text-[#FFCC1D]",
    title: "Personalized Learning",
    description:
      "Adaptive learning paths that adjust to each student's pace and learning style, ensuring optimal progress and understanding.",
  },
  {
    icon: Trophy,
    iconBg: "bg-gradient-to-br from-[#FFCC1D] to-yellow-400",
    iconColor: "text-[#116530]",
    title: "Gamified Experience",
    description:
      "Earn points, unlock achievements, and compete with friends while learning. Science has never been this exciting!",
  },
  {
    icon: Users,
    iconBg: "bg-gradient-to-br from-[#116530] to-green-600",
    iconColor: "text-[#FFCC1D]",
    title: "Collaborative Learning",
    description:
      "Work together on projects, share discoveries, and learn from peers in a safe, moderated environment.",
  },
  {
    icon: BarChart,
    iconBg: "bg-gradient-to-br from-[#FFCC1D] to-yellow-400",
    iconColor: "text-[#116530]",
    title: "Progress Tracking",
    description:
      "Detailed analytics and progress reports help students and parents track learning milestones and achievements.",
  },
  {
    icon: Shield,
    iconBg: "bg-gradient-to-br from-[#116530] to-green-600",
    iconColor: "text-[#FFCC1D]",
    title: "Safe Environment",
    description:
      "Child-safe platform with robust privacy protection and parental controls for peace of mind.",
  },
];

const teamMembers = [
  {
    name: "Manlapaz, Jhon Paul G.",
    role: "UI/UX Designer",
    description:
      "PhD in Science Education with 15 years of experience in curriculum development and interactive learning.",
    avatarBg: "bg-gradient-to-br from-[#FFCC1D] to-[#116530]",
    socials: [
      { name: "Email", icon: Mail },
      { name: "LinkedIn", icon: Linkedin },
    ],
  },
  {
    name: "Ibañez, Wilfredo III L.",
    role: "Lead Programmer",
    description:
      "Expert Android developer specializing in educational apps and user experience optimization for young learners.",
    avatarBg: "bg-gradient-to-br from-[#116530] to-[#FFCC1D]",
    socials: [
      { name: "Email", icon: Mail },
      { name: "GitHub", icon: Github },
    ],
  },
  {
    name: "Reyes, Oj G.",
    role: "Data Analyst",
    description:
      "Creative designer focused on child-friendly interfaces and engaging visual experiences that enhance learning.",
    avatarBg: "bg-gradient-to-br from-[#FFCC1D] via-[#E8E8CC] to-[#116530]",
    socials: [
      { name: "Email", icon: Mail },
      { name: "Dribbble", icon: Dribbble },
    ],
  },
  {
    name: "Banawan, Isaac Darry F.",
    role: "Document Specialist",
    description:
      "Creative designer focused on child-friendly interfaces and engaging visual experiences that enhance learning.",
    avatarBg: "bg-gradient-to-br from-[#FFCC1D] via-[#E8E8CC] to-[#116530]",
    socials: [
      { name: "Email", icon: Mail },
      { name: "Dribbble", icon: Dribbble },
    ],
  },
];

const footerSocials = [
  { name: "Facebook", icon: Facebook },
  { name: "Twitter", icon: Twitter },
  { name: "Instagram", icon: Instagram },
];

const footerLinks = [
  { href: "#hero", text: "Home" },
  { href: "#about", text: "About" },
  { href: "#developers", text: "Team" },
  { href: "#", text: "Privacy Policy" },
];

const contactInfo = [
  { type: "email", icon: Mail, value: "hello@thinksci.com" },
  { type: "phone", icon: Phone, value: "+1 (555) 123-4567" },
  { type: "address", icon: MapPin, value: "Education City, Learning District" },
];

// Methods
const toggleTheme = () => {
  isDark.value = !isDark.value;
  localStorage.setItem("theme", isDark.value ? "dark" : "light");
};

const toggleMobileMenu = () => {
  showMobileMenu.value = !showMobileMenu.value;
};

const closeMobileMenu = () => {
  showMobileMenu.value = false;
};

const smoothScroll = (event) => {
  event.preventDefault();
  const target = event.target.getAttribute("href");
  const element = document.querySelector(target);
  if (element) {
    element.scrollIntoView({ behavior: "smooth" });
  }
};

// Lifecycle
onMounted(() => {
  const savedTheme = localStorage.getItem("theme");
  if (savedTheme) {
    isDark.value = savedTheme === "dark";
  } else {
    isDark.value = window.matchMedia("(prefers-color-scheme: dark)").matches;
  }
});
</script>

<style scoped>
html {
  scroll-behavior: smooth;
}

/* Enhanced Animations */
@keyframes float {
  0%,
  100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-20px);
  }
}

@keyframes float-delayed {
  0%,
  100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-15px);
  }
}

@keyframes fade-in-up {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fade-in-right {
  from {
    opacity: 0;
    transform: translateX(30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes spin-slow {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

/* Animation Classes */
.animate-float {
  animation: float 6s ease-in-out infinite;
}

.animate-float-delayed {
  animation: float-delayed 8s ease-in-out infinite;
}

.animate-fade-in-up {
  animation: fade-in-up 0.6s ease-out forwards;
  opacity: 0;
}

.animate-fade-in-right {
  animation: fade-in-right 0.8s ease-out forwards;
  opacity: 0;
}

.animate-spin-slow {
  animation: spin-slow 20s linear infinite;
}

/* Animation Delays */
.animation-delay-200 {
  animation-delay: 200ms;
}

.animation-delay-400 {
  animation-delay: 400ms;
}

.animation-delay-600 {
  animation-delay: 600ms;
}

.animation-delay-800 {
  animation-delay: 800ms;
}

.animation-delay-1000 {
  animation-delay: 1000ms;
}

/* Custom Utilities */
.hover\:scale-102:hover {
  transform: scale(1.02);
}

.shadow-3xl {
  box-shadow: 0 35px 60px -12px rgba(0, 0, 0, 0.25);
}

/* Smooth transitions for better performance with longer durations */
* {
  transition-property: transform, opacity, color, background-color, border-color,
    box-shadow, filter, backdrop-filter;
  transition-timing-function: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  transition-duration: 0.4s;
}

/* Specific smooth hover transitions */
button,
.group,
a[href] {
  transition-property: all;
  transition-duration: 0.5s;
  transition-timing-function: cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

/* Extra smooth transitions for interactive elements */
.group:hover {
  transition-duration: 0.6s;
}

/* Smooth scale and transform transitions */
.hover\:scale-105:hover,
.hover\:scale-110:hover,
.group-hover\:scale-105,
.group-hover\:scale-110 {
  transition: transform 0.6s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

/* Smooth translate transitions */
.hover\:-translate-y-1:hover,
.hover\:-translate-y-2:hover,
.hover\:-translate-y-4:hover,
.hover\:-translate-y-6:hover,
.hover\:translate-x-1:hover,
.hover\:translate-x-2:hover {
  transition: transform 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

/* Smooth rotation transitions */
.group-hover\:rotate-3,
.group-hover\:rotate-6,
.hover\:rotate-0:hover,
.group-hover\:rotate-180,
.group-hover\:-rotate-12 {
  transition: transform 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

/* Smooth shadow transitions */
.hover\:shadow-lg:hover,
.hover\:shadow-xl:hover,
.hover\:shadow-2xl:hover,
.hover\:shadow-3xl:hover {
  transition: box-shadow 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

/* Smooth opacity transitions */
.opacity-0,
.group-hover\:opacity-100 {
  transition: opacity 0.6s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

/* Smooth background color transitions */
.hover\:bg-white:hover,
.hover\:from-green-600:hover,
.hover\:to-green-600:hover,
.hover\:bg-yellow-300:hover {
  transition: background-color 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

/* Smooth color transitions */
.hover\:text-yellow-500:hover,
.hover\:text-yellow-400:hover,
.hover\:text-yellow-600:hover,
.hover\:text-white:hover,
.group-hover\:text-yellow-600,
.group-hover\:text-white {
  transition: color 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

/* Backdrop blur fallback */
@supports not (backdrop-filter: blur(12px)) {
  .backdrop-blur-xl {
    background-color: rgba(255, 255, 255, 0.9);
  }
  .dark .backdrop-blur-xl {
    background-color: rgba(17, 24, 39, 0.9);
  }
}

/* Mobile optimizations */
@media (max-width: 768px) {
  .animate-fade-in-up,
  .animate-fade-in-right {
    animation-duration: 0.4s;
  }

  /* Slightly faster transitions on mobile for better performance */
  * {
    transition-duration: 0.3s;
  }

  button,
  .group,
  a[href] {
    transition-duration: 0.4s;
  }
}

/* Reduced motion for accessibility */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
</style>
