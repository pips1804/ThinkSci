<template>
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
            <span class="relative z-10 text-[#116530] dark:text-white">
              Team</span
            >
            <span
              class="absolute inset-0 bg-gradient-to-r from-yellow-400/30 to-green-400/30 rounded-lg blur-lg transform scale-110"
            ></span>
          </span>
        </h2>
        <p
          class="text-xl lg:text-2xl text-gray-600 dark:text-gray-300 max-w-4xl mx-auto leading-relaxed"
        >
          Passionate proponents working together to develop the e-learning
          application.
        </p>
      </div>

      <!-- Team Grid -->
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
              class="w-28 h-28 rounded-full overflow-hidden flex items-center justify-center mx-auto mb-6 shadow-xl group-hover:scale-110 transition-all duration-700"
            >
              <img
                :src="member.image"
                :alt="member.name"
                class="w-full h-full object-cover"
              />
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
              <a
                v-for="social in member.socials"
                :key="social.name"
                :href="social.url"
                target="_blank"
                rel="noopener noreferrer"
                class="p-3 bg-gray-100 dark:bg-gray-700 rounded-xl hover:bg-[#FFCC1D] hover:scale-110 hover:-translate-y-1 transition-all duration-500 shadow-md hover:shadow-lg"
                :aria-label="social.name"
              >
                <component
                  :is="social.icon"
                  class="w-5 h-5 text-[#116530] dark:text-gray-300 hover:text-white transition-colors duration-500"
                />
              </a>
            </div>
          </div>
        </div>
      </div>

      <!-- Call to Action -->
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
            <a
              href="https://www.mediafire.com/file/pelre1oy9w2aqyj/ThinkSci.apk/file"
              target="_blank"
              rel="noopener noreferrer"
              class="group bg-[#116530] hover:bg-green-600 text-white px-6 sm:px-8 py-3 sm:py-4 rounded-2xl font-semibold text-base sm:text-lg flex items-center justify-center space-x-2 sm:space-x-3 transition-all duration-600 ease-out transform hover:scale-105 hover:-translate-y-1 shadow-2xl hover:shadow-3xl"
            >
              <span
                class="relative z-10 flex items-center justify-center space-x-3"
              >
                <span>Get Started Now!</span>
                <Rocket
                  class="w-6 h-6 group-hover:translate-x-1 group-hover:-translate-y-1 transition-transform duration-500"
                />
              </span>
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import {
  User,
  Mail,
  Linkedin,
  Github,
  Dribbble,
  Rocket,
  FacebookIcon,
} from "lucide-vue-next";

// Data
const teamMembers = [
  {
    name: "Manlapaz, Jhon Paul G.",
    role: "UI/UX Designer",
    description: "Designs user-friendly and engaging interfaces for learners.",
    image: "/manlapaz.png",
    socials: [
      {
        name: "Email",
        icon: Mail,
        url: "https://mail.google.com/mail/?view=cm&fs=1&to=jhonpaulmanlapaz1804@gmail.com",
      },
      { name: "Github", icon: Github, url: "https://github.com/pips1804" },
      {
        name: "Facebook",
        icon: FacebookIcon,
        url: "https://www.facebook.com/jhonpaulgm/",
      },
    ],
  },
  {
    name: "Ibañez, Wilfredo III L.",
    role: "Lead Programmer",
    description:
      "Develops and manages the app’s core features and performance.",
    image: "/ibanez.png",
    socials: [
      {
        name: "Email",
        icon: Mail,
        url: "https://mail.google.com/mail/?view=cm&fs=1&to=ibanezwilfredo16@gmail.com",
      },
      {
        name: "Facebook",
        icon: FacebookIcon,
        url: "https://www.facebook.com/ibanezred15",
      },
    ],
  },
  {
    name: "Reyes, Oj G.",
    role: "Data Analyst",
    description: "Analyzes and interprets data to guide project decisions.",
    image: "/reyes.png",
    socials: [
      {
        name: "Email",
        icon: Mail,
        url: "https://mail.google.com/mail/?view=cm&fs=1&to=ojreyesgregorio@gmail.com",
      },
      {
        name: "Facebook",
        icon: FacebookIcon,
        url: "http://facebook.com/skipmakiw",
      },
    ],
  },
  {
    name: "Banawan, Isaac Darry F.",
    role: "Document Specialist",
    description: "Organizes and prepares clear project documentation.",
    image: "/banawan.png",
    socials: [
      {
        name: "Email",
        icon: Mail,
        url: "https://mail.google.com/mail/?view=cm&fs=1&to=isaacbanawan10@gmail.com",
      },
      {
        name: "Facebook",
        icon: FacebookIcon,
        url: "http://facebook.com/darryxc",
      },
    ],
  },
];
</script>
