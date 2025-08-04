<template>
  <footer class="bg-gray-900 text-white pt-24 pb-12 px-6 sm:px-8 lg:px-10">
    <div class="max-w-7xl mx-auto">
      <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-12">
        <div>
          <div class="flex items-center space-x-2 mb-6">
            <NuxtLink to="/">
              <img
                src="/assets/images/logo.png"
                alt="Mollage Media Logo"
                class="h-20 w-auto"
              />
            </NuxtLink>
          </div>
          <p class="text-gray-400 mb-6">
            Modern marketing solutions for forward-thinking brands. We help
            businesses grow through innovative strategies and data-driven
            approaches.
          </p>
          <div class="flex space-x-4">
            <a
              v-for="social in socialLinks"
              :key="social.name"
              :href="social.url"
              class="text-gray-400 hover:text-white rounded-full"
            >
              <Icon :name="social.icon" class="h-5 w-5" />
            </a>
          </div>
        </div>
        <div>
          <h3 class="text-lg font-semibold mb-6">Services</h3>
          <ul class="space-y-3">
            <li v-for="service in services.slice(0, 5)" :key="service.title">
              <a
                href="#"
                class="text-gray-400 hover:text-white transition-colors flex items-center"
              >
                <Icon
                  name="mdi:chevron-right"
                  class="h-4 w-4 mr-2 text-[#fe6600]"
                />
                {{ service.title }}
              </a>
            </li>
          </ul>
        </div>
        <div>
          <h3 class="text-lg font-semibold mb-6">Company</h3>
          <ul class="space-y-3">
            <li>
              <a
                href="/about"
                class="text-gray-400 hover:text-white transition-colors flex items-center"
              >
                <Icon
                  name="mdi:chevron-right"
                  class="h-4 w-4 mr-2 text-[#fe6600]"
                />
                About Us
              </a>
            </li>
            <li>
              <a
                href="/careers"
                class="text-gray-400 hover:text-white transition-colors flex items-center"
              >
                <Icon
                  name="mdi:chevron-right"
                  class="h-4 w-4 mr-2 text-[#fe6600]"
                />
                Careers
              </a>
            </li>
            <li>
              <a
                href="/blogs"
                class="text-gray-400 hover:text-white transition-colors flex items-center"
              >
                <Icon
                  name="mdi:chevron-right"
                  class="h-4 w-4 mr-2 text-[#fe6600]"
                />
                Blog
              </a>
            </li>
            <li>
              <a
                href="#"
                class="text-gray-400 hover:text-white transition-colors flex items-center"
              >
                <Icon
                  name="mdi:chevron-right"
                  class="h-4 w-4 mr-2 text-[#fe6600]"
                />
                Press
              </a>
            </li>
            <li>
              <a
                href="/contact"
                class="text-gray-400 hover:text-white transition-colors flex items-center"
              >
                <Icon
                  name="mdi:chevron-right"
                  class="h-4 w-4 mr-2 text-[#fe6600]"
                />
                Contact
              </a>
            </li>
          </ul>
        </div>
        <div>
          <h3 class="text-lg font-semibold mb-6">Newsletter</h3>
          <p class="text-gray-400 mb-6">
            Subscribe to our newsletter for the latest marketing tips and
            insights.
          </p>
          <form class="flex">
            <input
              type="email"
              placeholder="Your email"
              class="px-5 py-3 rounded-l-lg focus:outline-none bg-white text-gray-900 w-full"
            />
            <button
              type="submit"
              class="bg-gradient-to-r from-[#fe6600] to-[#541049] px-5 py-3 rounded-r-lg hover:shadow-lg transition-colors"
            >
              <Icon name="mdi:send" class="h-5 w-5 text-white" />
            </button>
          </form>
        </div>
      </div>
      <div
        class="border-t border-gray-800 mt-16 pt-8 flex flex-col md:flex-row justify-between items-center"
      >
        <p class="text-gray-400 text-sm">
          © 2025 Mollage Media. All rights reserved.
        </p>
        <div class="flex flex-wrap justify-center gap-x-6 gap-y-3 mt-4 md:mt-0">
          <a href="/privacy" class="text-gray-400 hover:text-white text-sm"
            >Privacy Policy</a
          >
          <a href="/terms" class="text-gray-400 hover:text-white text-sm"
            >Terms of Service</a
          >
          <a href="/cookies" class="text-gray-400 hover:text-white text-sm"
            >Cookies</a
          >
          <a href="#" class="text-gray-400 hover:text-white text-sm">Sitemap</a>
        </div>
      </div>
    </div>
  </footer>
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
