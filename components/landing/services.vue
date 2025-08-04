<template>
  <section
    id="services"
    class="py-24 px-6 sm:px-8 lg:px-10 max-w-7xl mx-auto"
  >
    <div class="text-center mb-20">
      <span
        class="inline-block px-4 py-2 bg-[#fff8f2] rounded-full text-[#fe6600] font-medium mb-4"
        >Our Services</span
      >
      <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold mb-6">
        Tailored
        <span
          class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent"
          >Solutions</span
        >
        For Growth
      </h2>
      <p class="max-w-2xl mx-auto text-xl text-gray-600">
        We offer comprehensive marketing solutions designed to scale your
        business effectively.
      </p>
    </div>

    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
      <div
        v-for="(service, index) in services"
        :key="index"
        class="bg-white p-8 rounded-2xl shadow-sm hover:shadow-lg transition-all duration-300 border border-gray-100 hover:border-transparent service-card group"
      >
        <div
          class="bg-gradient-to-r from-[#fff0e6] to-[#f3e8f1] w-16 h-16 rounded-2xl flex items-center justify-center mb-6"
        >
          <Icon :name="service.icon" class="h-8 w-8 text-[#fe6600]" />
        </div>
        <h3 class="text-2xl font-bold mb-4 text-gray-900">
          {{ service.title }}
        </h3>
        <p class="text-gray-600 mb-6">{{ service.description }}</p>
        <a
          href="#"
          class="inline-flex items-center text-[#fe6600] font-medium group-hover:underline"
        >
          Learn more
          <Icon name="mdi:arrow-right" class="ml-2 h-5 w-5" />
        </a>
      </div>
    </div>
  </section>
</template>

<script>
import { Icon } from "@iconify/vue";

export default {
  name: "Services",
  components: { Icon },
  data() {
    return {
      services: [
        {
          icon: "mdi:bullhorn-outline",
          title: "Digital Advertising",
          description:
            "Targeted campaigns across social media, search engines, and display networks to drive conversions and maximize ROI.",
        },
        {
          icon: "mdi:chart-bar",
          title: "SEO Optimization",
          description:
            "Improve your search rankings and organic traffic with our proven SEO strategies and technical expertise.",
        },
        {
          icon: "mdi:pen",
          title: "Content Creation",
          description:
            "Engaging content that tells your brand story, connects with your audience, and drives action.",
        },
        {
          icon: "mdi:cellphone",
          title: "Social Media",
          description:
            "Complete management of your social presence with data-driven content strategies and community engagement.",
        },
        {
          icon: "mdi:video",
          title: "Video Production",
          description:
            "Professional video content that captivates your audience, tells your story, and boosts engagement.",
        },
        {
          icon: "mdi:palette",
          title: "Brand Strategy",
          description:
            "Comprehensive branding solutions to establish your unique market position and visual identity.",
        },
      ],
    };
  },
};
</script>