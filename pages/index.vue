<template>
  <div class="min-h-screen bg-gray-50 text-gray-900 font-sans antialiased">
    <!-- Gradient Background Elements -->
    <div class="fixed inset-0 overflow-hidden pointer-events-none">
      <div
        class="absolute top-0 left-1/4 w-96 h-96 bg-[#fe6600] rounded-full mix-blend-multiply filter blur-3xl opacity-20"
      ></div>
      <div
        class="absolute top-1/3 right-1/4 w-96 h-96 bg-[#541049] rounded-full mix-blend-multiply filter blur-3xl opacity-20"
      ></div>
    </div>

    <!-- Navigation -->
    <LandingNav />

    <main class="relative z-10">
      <!-- Hero Section -->
      <LandingHero />

      <!-- Client logos -->
      <!-- <div class="py-16 bg-white">
        <div class="max-w-7xl mx-auto px-6 sm:px-8 lg:px-10">
          <p
            class="text-center text-gray-500 mb-10 uppercase tracking-wider text-sm font-medium"
          >
            Trusted by innovative brands worldwide
          </p>
          <div
            class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-6 gap-8 items-center"
          >
            <div
              v-for="i in 6"
              :key="i"
              class="flex items-center justify-center h-16"
            >
              <img
                :src="`https://images.unsplash.com/photo-1599305445671-ac291c95aaa9?ixlib=rb-1.2.1&auto=format&fit=crop&w=200&h=100&q=80&fit=max&txt=Client+${i}&txtfont=bold&txtsize=48&txtclr=333333&bg=ffffff`"
                alt="Client logo"
                class="h-8 object-contain opacity-70 hover:opacity-100 transition-opacity grayscale hover:grayscale-0"
              />
            </div>
          </div>
        </div>
      </div> -->

      <!-- Services Section -->
      <LandingServices />

      <!-- Portfolio Showcase -->
      <LandingWork />

      <!-- Stats Section -->
      <section
        class="py-24 bg-gradient-to-r from-[#fe6600] to-[#541049] text-white"
      >
        <div class="max-w-7xl mx-auto px-6 sm:px-8 lg:px-10">
          <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
            <div v-for="stat in stats" :key="stat.label" class="text-center">
              <p class="text-5xl font-bold mb-3">{{ stat.value }}</p>
              <p class="text-lg font-medium opacity-90">{{ stat.label }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- Testimonials Section -->
      <LandingTestimonial />

      <!-- Team Section -->
      <LandingAbout />

      <!-- CTA Section -->
      <section
        class="py-24 bg-gradient-to-r from-[#fe6600] to-[#541049] text-white"
      >
        <div class="max-w-4xl mx-auto px-6 sm:px-8 lg:px-10 text-center">
          <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold mb-6">
            Ready to Transform Your
            <span
              class="bg-gradient-to-r from-white to-[#fff0e6] bg-clip-text text-transparent"
              >Business?</span
            >
          </h2>
          <p class="text-xl mb-10 max-w-2xl mx-auto opacity-90">
            Schedule a free consultation with our team to discuss how we can
            help you achieve your marketing goals.
          </p>
          <button
            class="relative inline-flex items-center justify-center px-8 py-3.5 bg-white text-[#fe6600] rounded-xl hover:shadow-lg transition-all hover:scale-[1.02] group font-medium"
          >
            <span>Book a Free Strategy Session</span>
            <span
              class="ml-3 inline-flex items-center justify-center transform group-hover:translate-x-1 transition-transform"
            >
              <Icon name="mdi:calendar-arrow-right" class="h-5 w-5" />
            </span>
            <span
              class="absolute inset-0 rounded-xl border-2 border-transparent group-hover:border-white/30 transition-all duration-300"
            ></span>
          </button>
        </div>
      </section>

      <!-- Contact Section -->
      <LandingContact />
    </main>

    <!-- Footer -->
   <LandingFooter />

   
  </div>
</template>

<script>
// The script remains the same as it is color-agnostic.
import { Icon } from "@iconify/vue";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
  name: "MarketingLandingPage",
  components: { Icon },
  data() {
    return {
      stats: [
        { value: "87%", label: "Client Growth Rate" },
        { value: "3.5x", label: "Average ROI" },
        { value: "500+", label: "Brands Helped" },
        { value: "24/7", label: "Support Available" },
      ],

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
      socialLinks: [
        { name: "twitter", icon: "mdi:twitter", url: "#" },
        { name: "facebook", icon: "mdi:facebook", url: "#" },
        { name: "instagram", icon: "mdi:instagram", url: "#" },
        { name: "linkedin", icon: "mdi:linkedin", url: "#" },
      ],
    };
  },
  mounted() {
    gsap.registerPlugin(ScrollTrigger);

    gsap.from(".hero-content", {
      duration: 1,
      y: 50,
      opacity: 0,
      delay: 0.2,
      ease: "power3.out",
    });

    gsap.from(".hero-image", {
      duration: 1.2,
      x: 50,
      opacity: 0,
      delay: 0.4,
      ease: "power3.out",
    });

    gsap.utils.toArray(".service-card").forEach((card, i) => {
      gsap.from(card, {
        scrollTrigger: {
          trigger: card,
          start: "top 85%",
          toggleActions: "play none none none",
        },
        y: 50,
        opacity: 0,
        duration: 0.8,
        delay: i * 0.1,
        ease: "power3.out",
      });
    });

    gsap.utils.toArray(".team-member").forEach((member, i) => {
      gsap.from(member, {
        scrollTrigger: {
          trigger: member,
          start: "top 85%",
          toggleActions: "play none none none",
        },
        y: 30,
        opacity: 0,
        duration: 0.6,
        delay: i * 0.1,
        ease: "back.out(1.2)",
      });
    });
  },
  methods: {
    submitForm() {
      console.log("Form submitted:", this.form);
      alert("Thank you for your message! We will get back to you soon.");
      this.form = {
        name: "",
        email: "",
        service: "",
        message: "",
      };
    },
  },
};
</script>

<style>
/* Custom styles */
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap");

body {
  font-family: "Inter", sans-serif;
}

/* Smooth scrolling for anchor links */
html {
  scroll-behavior: smooth;
}

/* Custom select arrow */
select {
  background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 20 20'%3e%3cpath stroke='%236b7280' stroke-linecap='round' stroke-linejoin='round' stroke-width='1.5' d='M6 8l4 4 4-4'/%3e%3c/svg%3e");
  background-position: right 0.75rem center;
  background-repeat: no-repeat;
  background-size: 1.25em 1.25em;
  padding-right: 2.5rem;
  -webkit-print-color-adjust: exact;
  print-color-adjust: exact;
}
</style>
