<template>
  <div
    :class="{ dark: isDark }"
    class="min-h-screen transition-colors duration-300"
  >
    <!-- Navigation Component -->
    <NavBar
      :isDark="isDark"
      :showMobileMenu="showMobileMenu"
      @toggle-theme="toggleTheme"
      @toggle-mobile-menu="toggleMobileMenu"
      @close-mobile-menu="closeMobileMenu"
    />

    <!-- Hero Section Component -->
    <HeroSection />

    <!-- About Section Component -->
    <AboutSection />

    <!-- Developers Section Component -->
    <DevelopersSection />

    <!-- Footer Component -->
    <FooterSection />
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import NavBar from "./components/NavBar.vue";
import HeroSection from "./components/HeroSection.vue";
import AboutSection from "./components/AboutSection.vue";
import DevelopersSection from "./components/DevelopersSection.vue";
import FooterSection from "./components/FooterSection.vue";

// Reactive state
const isDark = ref(true);
const showMobileMenu = ref(false);

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
/* Global styles remain here or move to a separate CSS file */
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

@keyframes float-random {
  0%,
  100% {
    transform: translateY(0px) translateX(0px) rotate(0deg);
  }
  25% {
    transform: translateY(-10px) translateX(5px) rotate(90deg);
  }
  50% {
    transform: translateY(-20px) translateX(-5px) rotate(180deg);
  }
  75% {
    transform: translateY(-10px) translateX(10px) rotate(270deg);
  }
}

@keyframes bubble-effect {
  0% {
    transform: scale(1);
    opacity: 0.7;
  }
  50% {
    transform: scale(1.1);
    opacity: 0.9;
  }
  100% {
    transform: scale(1);
    opacity: 0.7;
  }
}

@keyframes particle-burst {
  0% {
    transform: scale(0) rotate(0deg);
    opacity: 0;
  }
  50% {
    transform: scale(1) rotate(180deg);
    opacity: 1;
  }
  100% {
    transform: scale(0) rotate(360deg);
    opacity: 0;
  }
}

/* Animation Classes */
:deep(.animate-float) {
  animation: float 6s ease-in-out infinite;
}

:deep(.animate-float-delayed) {
  animation: float-delayed 8s ease-in-out infinite;
}

:deep(.animate-fade-in-up) {
  animation: fade-in-up 0.6s ease-out forwards;
  opacity: 0;
}

:deep(.animate-fade-in-right) {
  animation: fade-in-right 0.8s ease-out forwards;
  opacity: 0;
}

:deep(.animate-float-random) {
  animation: float-random 6s ease-in-out infinite;
}

:deep(.animate-bubble) {
  animation: bubble-effect 3s ease-in-out infinite;
}

:deep(.animate-particle-burst) {
  animation: particle-burst 2s ease-out infinite;
}

:deep(.animate-spin-slow) {
  animation: spin-slow 20s linear infinite;
}

/* Animation Delays */
:deep(.animation-delay-200) {
  animation-delay: 200ms;
}
:deep(.animation-delay-400) {
  animation-delay: 400ms;
}
:deep(.animation-delay-600) {
  animation-delay: 600ms;
}
:deep(.animation-delay-800) {
  animation-delay: 800ms;
}
:deep(.animation-delay-1000) {
  animation-delay: 1000ms;
}

/* Custom Utilities */
:deep(.hover\:scale-102:hover) {
  transform: scale(1.02);
}
:deep(.shadow-3xl) {
  box-shadow: 0 35px 60px -12px rgba(0, 0, 0, 0.25);
}

/* Smooth transitions */
:deep(*) {
  transition-property: transform, opacity, color, background-color, border-color,
    box-shadow, filter, backdrop-filter;
  transition-timing-function: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  transition-duration: 0.4s;
}

:deep(button),
:deep(.group),
:deep(a[href]) {
  transition-property: all;
  transition-duration: 0.5s;
  transition-timing-function: cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

/* Backdrop blur fallback */
@supports not (backdrop-filter: blur(12px)) {
  :deep(.backdrop-blur-xl) {
    background-color: rgba(255, 255, 255, 0.9);
  }
  .dark :deep(.backdrop-blur-xl) {
    background-color: rgba(17, 24, 39, 0.9);
  }
}

/* Reduced motion for accessibility */
@media (prefers-reduced-motion: reduce) {
  :deep(*),
  :deep(*::before),
  :deep(*::after) {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
</style>
