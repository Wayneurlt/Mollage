<template>
  <section id="about" class="py-24 bg-gray-50 px-6 sm:px-8 lg:px-10">
    <div class="max-w-7xl mx-auto">
      <div class="text-center mb-20">
        <span
          class="inline-block px-4 py-2 bg-[#fff8f2] rounded-full text-[#fe6600] font-medium mb-4"
          >Our Team</span
        >
        <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold mb-6">
          Meet The
          <span
            class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent"
            >Experts</span
          >
        </h2>
        <p class="max-w-2xl mx-auto text-xl text-gray-600">
          Our talented team of marketing experts is ready to bring your vision
          to life.
        </p>
      </div>

      <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-8">
        <div
          v-for="(member, index) in team"
          :key="index"
          class="bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-lg transition-shadow text-center team-member group"
        >
          <div class="relative overflow-hidden h-80">
            <img
              :src="member.image"
              :alt="member.name"
              class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
            />
            <div
              class="absolute inset-0 bg-gradient-to-t from-black/50 to-transparent opacity-0 group-hover:opacity-100 transition-opacity flex items-end p-6"
            >
              <div class="w-full text-left">
                <p class="text-white text-sm">{{ member.bio }}</p>
              </div>
            </div>
          </div>
          <div class="p-6">
            <h3 class="text-xl font-bold text-gray-900">
              {{ member.name }}
            </h3>
            <p class="text-[#fe6600] mb-4">{{ member.position }}</p>
            <div class="flex justify-center space-x-4">
              <a
                v-for="social in member.social"
                :key="social.name"
                :href="social.url"
                class="text-gray-400 hover:text-[#fe6600] transition-colors p-2 rounded-full bg-gray-100 hover:bg-[#fff0e6]"
              >
                <Icon :name="social.icon" class="h-5 w-5" />
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { Icon } from "@iconify/vue";

export default {
  name: "About",
  components: { Icon },
  data() {
    return {
      team: [
        {
          name: "Mollage",
          position: "CEO & Founder",
          bio: "Marketing strategist with 12+ years of experience building brands and driving growth for Fortune 500 companies and startups alike.",
          image:
            "data:image/jpeg;base64,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",
          social: [
            { name: "twitter", icon: "mdi:twitter", url: "#" },
            { name: "linkedin", icon: "mdi:linkedin", url: "#" },
          ],
        },
        {
          name: "Jamie Smith",
          position: "Creative Director",
          bio: "Design visionary with a passion for storytelling through visuals. Former art director at major advertising agencies.",
          image:
            "https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=400&q=80&fit=max",
          social: [
            { name: "twitter", icon: "mdi:twitter", url: "#" },
            { name: "dribbble", icon: "mdi:dribbble", url: "#" },
          ],
        },
        {
          name: "Taylor Wong",
          position: "Digital Strategist",
          bio: "Data-driven marketer specializing in performance campaigns with expertise in analytics and conversion optimization.",
          image:
            "https://images.unsplash.com/photo-1554151228-14d9def656e4?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=400&q=80&fit=max",
          social: [
            { name: "linkedin", icon: "mdi:linkedin", url: "#" },
            { name: "github", icon: "mdi:github", url: "#" },
          ],
        },
        {
          name: "Morgan Lee",
          position: "Content Manager",
          bio: "Wordsmith crafting compelling narratives that resonate with audiences and drive meaningful engagement.",
          image:
            "https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=400&q=80&fit=max",
          social: [
            { name: "twitter", icon: "mdi:twitter", url: "#" },
            { name: "medium", icon: "mdi:medium", url: "#" },
          ],
        },
      ],
    };
  },
};
</script>
