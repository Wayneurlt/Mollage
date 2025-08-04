<template>
  <section id="portfolio" class="py-24 bg-gray-50 px-6 sm:px-8 lg:px-10">
    <div class="max-w-7xl mx-auto">
      <div class="text-center mb-20">
        <span
          class="inline-block px-4 py-2 bg-[#fff8f2] rounded-full text-[#fe6600] font-medium mb-4"
          >Our Work</span
        >
        <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold mb-6">
          Success
          <span
            class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent"
            >Stories</span
          >
        </h2>
        <p class="max-w-2xl mx-auto text-xl text-gray-600">
          Explore how we've transformed brands and driven exceptional results.
        </p>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="(project, index) in portfolio"
          :key="index"
          class="group portfolio-item relative overflow-hidden rounded-2xl shadow-lg hover:shadow-xl transition-shadow h-96"
        >
          <img
            :src="project.image"
            :alt="project.title"
            class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
          />
          <div
            class="absolute inset-0 bg-gradient-to-t from-black/60 via-black/30 to-transparent flex flex-col justify-end p-8 opacity-0 group-hover:opacity-100 transition-opacity duration-300"
          >
            <div>
              <span
                class="inline-block px-3 py-1 bg-white/90 backdrop-blur-sm rounded-full text-xs font-medium mb-3"
                >{{ project.category }}</span
              >
              <h3 class="text-white text-2xl font-bold mb-2">
                {{ project.title }}
              </h3>
              <p class="text-gray-200">{{ project.description }}</p>
            </div>
          </div>
          <div
            class="absolute inset-0 flex items-center justify-center opacity-100 group-hover:opacity-0 transition-opacity duration-300 bg-black/10"
          >
            <h3
              class="text-white text-2xl font-bold text-center px-4 drop-shadow-lg"
            >
              {{ project.title }}
            </h3>
          </div>
        </div>
      </div>

      <div class="text-center mt-16">
        <button
          class="relative inline-flex items-center px-8 py-3.5 bg-white text-gray-800 rounded-xl border border-gray-200 hover:border-gray-300 hover:shadow-lg transition-all group"
        >
          <span>View All Case Studies</span>
          <span
            class="ml-3 inline-flex items-center justify-center transform group-hover:translate-x-1 transition-transform"
          >
            <Icon name="mdi:arrow-right" class="h-5 w-5" />
          </span>
          <span
            class="absolute inset-0 rounded-xl border-2 border-transparent group-hover:border-gray-200/50 transition-all duration-300"
          ></span>
        </button>
      </div>
    </div>
  </section>
</template>

<script>
import { Icon } from "@iconify/vue";

export default {
  name: "Work",
  components: { Icon },
  data() {
    return {
      portfolio: [
        {
          title: "EcoFashion Brand Launch",
          category: "Brand Strategy",
          image:
            "https://images.unsplash.com/photo-1492707892479-7bc8d5a4ee93?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80",
          description:
            "360° brand strategy that increased online sales by 240% in first quarter",
        },
        {
          title: "Tech Startup Campaign",
          category: "Digital Advertising",
          image:
            "https://images.unsplash.com/photo-1551288049-bebda4e38f71?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80",
          description:
            "Performance marketing campaign with 5.2x ROI and 35% lower CAC",
        },
        {
          title: "Restaurant Rebranding",
          category: "Visual Identity",
          image:
            "https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80",
          description:
            "Complete visual rebrand resulting in 3x more reservations",
        },
        {
          title: "Health App Marketing",
          category: "Influencer Campaign",
          image:
            "https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80",
          description:
            "Influencer strategy that drove 50,000+ app downloads in 30 days",
        },
        {
          title: "B2B SaaS Growth",
          category: "Content Marketing",
          image:
            "https://images.unsplash.com/photo-1552664730-d307ca884978?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80",
          description:
            "Content engine that increased organic traffic by 320% year-over-year",
        },
        {
          title: "Nonprofit Awareness",
          category: "Video Production",
          image:
            "https://images.unsplash.com/photo-1501386761578-eac5c94b800a?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80",
          description: "Emotional storytelling campaign that doubled donations",
        },
      ],
    };
  },
};
</script>