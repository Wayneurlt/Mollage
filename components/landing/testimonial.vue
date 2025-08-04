<template>
  <section class="py-24 px-6 sm:px-8 lg:px-10 max-w-7xl mx-auto">
    <div class="text-center mb-20">
      <span
        class="inline-block px-4 py-2 bg-[#fff8f2] rounded-full text-[#fe6600] font-medium mb-4"
        >Testimonials</span
      >
      <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold mb-6">
        What Our
        <span
          class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent"
          >Clients</span
        >
        Say
      </h2>
      <p class="max-w-2xl mx-auto text-xl text-gray-600">
        Don't just take our word for it. Here's what our clients say about
        working with us.
      </p>
    </div>

    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
      <div
        v-for="(testimonial, index) in testimonials"
        :key="index"
        class="bg-white p-8 rounded-2xl shadow-sm border border-gray-100 hover:shadow-md transition-all"
      >
        <div class="flex items-center mb-6">
          <div class="flex-shrink-0">
            <img
              :src="testimonial.avatar"
              :alt="testimonial.name"
              class="h-14 w-14 rounded-full object-cover"
            />
          </div>
          <div class="ml-4">
            <h4 class="font-bold text-lg">{{ testimonial.name }}</h4>
            <p class="text-gray-500">{{ testimonial.position }}</p>
          </div>
        </div>
        <p class="text-gray-700 mb-6">"{{ testimonial.quote }}"</p>
        <div class="flex items-center">
          <div class="flex text-[#fe6600] mr-3">
            <Icon v-for="i in 5" :key="i" name="mdi:star" class="h-5 w-5" />
          </div>
          <span class="text-sm text-gray-500">Verified Client</span>
        </div>
      </div>
    </div>
  </section>
</template>
<
<script>
import { Icon } from "@iconify/vue";

export default {
  name: "testimonial",
  components: { Icon },
  data() {
    return {
      testimonials: [
        {
          name: "Sarah Johnson",
          position: "CEO, GreenLife",
          quote:
            "Mollage Media transformed our digital presence. Our engagement rates tripled within the first three months of working with them. Their strategic approach and creative execution delivered results beyond our expectations.",
          avatar:
            "https://images.pexels.com/photos/3769021/pexels-photo-3769021.jpeg",
        },
        {
          name: "Michael Chen",
          position: "Marketing Director, TechNova",
          quote:
            "Their data-driven approach to our ad campaigns reduced our CAC by 40% while increasing conversion rates significantly. The team is incredibly responsive and brings innovative ideas to every meeting.",
          avatar:
            "https://images.pexels.com/photos/17243662/pexels-photo-17243662.jpeg",
        },
        {
          name: "Emily Rodriguez",
          position: "Founder, UrbanEats",
          quote:
            "The brand strategy they developed perfectly captured our vision and helped us stand out in a crowded market. Our revenue increased by 150% in the first year after rebranding with Mollage.",
          avatar:
            "https://images.pexels.com/photos/15647623/pexels-photo-15647623.jpeg",
        },
      ],
    };
  },
};
</script>
