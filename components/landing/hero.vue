<template>
  <section
    id="home"
    class="pt-32 pb-24 px-6 sm:px-8 lg:px-10 max-w-7xl mx-auto"
  >
    <div class="grid lg:grid-cols-2 gap-16 items-center">

      <div class="space-y-8 hero-content ">
        <div
          class="inline-flex items-center px-4 py-2 bg-[#fff8f2] rounded-full"
        >
          <span class="text-sm font-medium text-[#fe6600]"
            >Modern Marketing Solutions</span
          >
        </div>
        <h1
          class="text-4xl md:text-5xl lg:text-6xl font-bold leading-tight tracking-tight"
        >
          Transform Your
          <span
            class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent"
            >Brand Presence</span
          >
        </h1>
        <p class="text-xl text-gray-600 max-w-2xl">
          Mollage Media delivers cutting-edge digital strategies that drive
          measurable results and elevate your brand above the competition.
        </p>
        <div
          class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-6"
        >
          <button
            class="relative inline-flex items-center justify-center px-8 py-3.5 bg-gradient-to-r from-[#fe6600] to-[#541049] text-white rounded-xl hover:shadow-lg transition-all hover:scale-[1.02] group"
          >
            <span>Start Your Journey</span>
            <span
              class="ml-3 inline-flex items-center justify-center transform group-hover:translate-x-1 transition-transform"
            >
              <Icon name="mdi:arrow-right" class="h-5 w-5" />
            </span>
            <span
              class="absolute inset-0 rounded-xl border-2 border-transparent group-hover:border-white/30 transition-all duration-300"
            ></span>
          </button>
          <button
            class="relative inline-flex items-center justify-center px-8 py-3.5 bg-white text-gray-800 rounded-xl border border-gray-200 hover:border-gray-300 hover:shadow-md transition-all"
          >
            <span>How We Work</span>
            <span class="ml-3 inline-flex items-center justify-center">
              <Icon name="mdi:play-circle-outline" class="h-5 w-5" />
            </span>
          </button>
        </div>
        <div class="pt-6 flex items-center space-x-6">
          <div class="flex items-center -space-x-2">
            <img
              v-for="(img, i) in teamAvatars"
              :key="i"
              :src="img"
              class="w-10 h-10 rounded-full border-2 border-white"
            />
          </div>
          <div>
            <p class="text-sm font-medium text-gray-700">
              Trusted by 50+ brands
            </p>
            <div class="flex items-center mt-1">
              <Icon
                v-for="i in 5"
                :key="i"
                name="mdi:star"
                class="h-4 w-4 text-[#fe6600]"
              />
              <span class="ml-2 text-sm text-gray-600">4.8 (100+ reviews)</span>
            </div>
          </div>
        </div> 
      </div>

      <div class="relative hero-image ">
        <div class="relative rounded-2xl overflow-hidden shadow-2xl">
          <img
            src="https://images.pexels.com/photos/9490623/pexels-photo-9490623.jpeg"
            alt="Marketing team working"
            class="w-full h-auto object-cover"
          />
          <div
            class="absolute inset-0 bg-gradient-to-t from-black/30 to-transparent"
          ></div>
        </div>
        <div
          class="absolute -bottom-6 -left-6 bg-white p-5 rounded-xl shadow-xl border border-gray-100"
        >
          <div class="flex items-center space-x-4">
            <div class="bg-[#fff0e6] p-3 rounded-lg">
              <Icon name="mdi:trending-up" class="h-6 w-6 text-[#fe6600]" />
            </div>
            <div>
              <p class="text-2xl font-bold text-gray-900">+87%</p>
              <p class="text-sm text-gray-500">Average client growth</p>
            </div>
          </div>
        </div>
        <div
          class="absolute -top-6 -right-6 bg-white p-5 rounded-xl shadow-xl border border-gray-100"
        >
          <div class="flex items-center space-x-4">
            <div class="bg-[#f3e8f1] p-3 rounded-lg">
              <Icon name="mdi:chart-pie" class="h-6 w-6 text-[#541049]" />
            </div>
            <div>
              <p class="text-2xl font-bold text-gray-900">3.5x</p>
              <p class="text-sm text-gray-500">ROI improvement</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { Icon } from "@iconify/vue";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
  name: "HeroSection",
  components: {
    Icon,
  },
  data() {
    return {
      teamAvatars: [
        "https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?ixlib=rb-1.2.1&auto=format&fit=crop&w=100&h=100&q=80&fit=max",
        "https://images.unsplash.com/photo-1560250097-0b93528c311a?ixlib=rb-1.2.1&auto=format&fit=crop&w=100&h=100&q=80&fit=max",
        "https://images.unsplash.com/photo-1554151228-14d9def656e4?ixlib=rb-1.2.1&auto=format&fit=crop&w=100&h=100&q=80&fit=max",
        "https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&auto=format&fit=crop&w=100&h=100&q=80&fit=max",
      ],
    };
  },
  mounted() {
    gsap.registerPlugin(ScrollTrigger);

    gsap.from(".hero-content", {
      duration: 1,
      y: 50,
      opacity: 50,
      delay: 0.2,
      ease: "power3.out",
    });

    gsap.from(".hero-image", {
      duration: 1.2,
      x: 50,
      opacity: 50,
      delay: 0.4,
      ease: "power3.out",
    });
  },
};
</script>
