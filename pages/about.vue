<template>
  <div class="min-h-screen bg-gray-50 text-gray-900 font-sans antialiased">
    <!-- Gradient Background Elements -->
    <div class="fixed inset-0 overflow-hidden pointer-events-none">
      <div
        class="absolute -top-20 right-0 w-96 h-96 bg-[#fe6600] rounded-full mix-blend-multiply filter blur-3xl opacity-20"
      ></div>
      <div
        class="absolute top-1/2 left-0 w-96 h-96 bg-[#541049] rounded-full mix-blend-multiply filter blur-3xl opacity-20"
      ></div>
    </div>

    <!-- Navigation (Reused from landing page for consistency) -->
   <LandingNav />

    <main class="relative z-10">
      <!-- About Hero Section -->
      <section class="pt-40 pb-24 text-center bg-white/50">
        <div class="max-w-4xl mx-auto px-6">
          <div class="about-hero-content">
            <h1 class="text-4xl md:text-5xl lg:text-6xl font-bold leading-tight tracking-tight mb-6">
              The Creative Force Behind
              <span class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent">Game-Changing Brands</span>
            </h1>
            <p class="text-xl text-gray-600 max-w-2xl mx-auto">
              We are a team of strategists, creatives, and innovators passionate about building brands and driving results. Learn more about our story, our values, and the people who make it all happen.
            </p>
          </div>
        </div>
      </section>

      <!-- Mission & Vision Section -->
      <section class="py-24 px-6 sm:px-8 lg:px-10">
        <div class="max-w-7xl mx-auto grid lg:grid-cols-2 gap-16 items-center">
          <div class="mission-image">
            <img src="https://images.unsplash.com/photo-1521737711867-e3b97375f902?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80" alt="Team collaborating" class="rounded-2xl shadow-xl w-full h-auto object-cover">
          </div>
          <div class="mission-content">
            <span class="inline-block px-4 py-2 bg-[#fff8f2] rounded-full text-[#fe6600] font-medium mb-4">Our Mission</span>
            <h2 class="text-3xl md:text-4xl font-bold mb-6">
              Empowering Brands Through Strategy & Creativity
            </h2>
            <p class="text-lg text-gray-600 mb-4">
              Our mission is to empower brands to achieve sustainable growth through a fusion of data-driven strategy and bold creativity. We believe in building partnerships, not just campaigns.
            </p>
            <p class="text-lg text-gray-600">
              We strive to be more than just a marketing agency; we aim to be an extension of your team, dedicated to understanding your challenges and celebrating your victories as our own.
            </p>
          </div>
        </div>
      </section>

      <!-- Timeline Section -->
      <section class="py-24 bg-white px-6 sm:px-8 lg:px-10">
        <div class="max-w-5xl mx-auto">
          <div class="text-center mb-20">
            <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold mb-6">
              Our <span class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent">Journey</span>
            </h2>
            <p class="max-w-2xl mx-auto text-xl text-gray-600">
              From a small startup to a leading digital agency, our journey has been one of passion and perseverance.
            </p>
          </div>
          <div class="relative">
            <!-- The vertical line -->
            <div class="absolute left-1/2 h-full w-0.5 bg-gray-200 hidden lg:block"></div>
            <!-- Timeline items -->
            <div v-for="(item, index) in timeline" :key="index" class="timeline-item mb-12 flex lg:justify-between items-center w-full" :class="index % 2 === 0 ? 'lg:flex-row-reverse' : ''">
              <div class="hidden lg:block w-5/12"></div>
              <div class="z-10 flex items-center justify-center">
                <div class="w-8 h-8 bg-[#fe6600] rounded-full flex items-center justify-center">
                   <Icon :name="item.icon" class="h-5 w-5 text-white" />
                </div>
              </div>
              <div class="bg-gray-50 border border-gray-100 rounded-xl shadow-md p-6 w-full lg:w-5/12">
                <span class="font-bold text-sm text-[#541049] mb-2 inline-block">{{ item.year }}</span>
                <h3 class="font-bold text-xl mb-2">{{ item.title }}</h3>
                <p class="text-gray-600">{{ item.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Core Values Section -->
      <section class="py-24 px-6 sm:px-8 lg:px-10">
        <div class="max-w-7xl mx-auto">
          <div class="text-center mb-20">
             <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold mb-6">
              The Principles That <span class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent">Guide Us</span>
            </h2>
            <p class="max-w-2xl mx-auto text-xl text-gray-600">
              Our values are the bedrock of our culture and the driving force behind our success.
            </p>
          </div>
          <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
            <div v-for="value in coreValues" :key="value.title" class="text-center p-8 bg-white rounded-2xl shadow-sm hover:shadow-lg transition-shadow value-card">
              <div class="inline-block p-4 bg-[#fff0e6] rounded-xl mb-6">
                <Icon :name="value.icon" class="h-8 w-8 text-[#fe6600]" />
              </div>
              <h3 class="text-2xl font-bold mb-3">{{ value.title }}</h3>
              <p class="text-gray-600">{{ value.description }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- Stats Section (Reused) -->
      <section class="py-24 bg-gradient-to-r from-[#fe6600] to-[#541049] text-white">
        <div class="max-w-7xl mx-auto px-6 sm:px-8 lg:px-10">
          <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
            <div v-for="stat in stats" :key="stat.label" class="text-center">
              <p class="text-5xl font-bold mb-3">{{ stat.value }}</p>
              <p class="text-lg font-medium opacity-90">{{ stat.label }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- Team Section (Reused) -->
      <section id="team" class="py-24 bg-gray-50 px-6 sm:px-8 lg:px-10">
        <div class="max-w-7xl mx-auto">
          <div class="text-center mb-20">
            <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold mb-6">
              Meet The <span class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent">Experts</span>
            </h2>
            <p class="max-w-2xl mx-auto text-xl text-gray-600">
              Our talented team of marketing experts is ready to bring your vision to life.
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
              </div>
              <div class="p-6">
                <h3 class="text-xl font-bold text-gray-900">{{ member.name }}</h3>
                <p class="text-[#fe6600] mb-4">{{ member.position }}</p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Careers CTA Section -->
      <section class="py-24 bg-gradient-to-r from-[#541049] to-[#3a0b34]">
        <div class="max-w-4xl mx-auto px-6 text-center">
           <h2 class="text-3xl md:text-4xl font-bold text-white mb-6">
             Want to Join Our Team?
            </h2>
          <p class="text-xl text-gray-300 mb-10 max-w-2xl mx-auto">
            We're always looking for passionate and talented individuals to join our mission. Explore our open positions and find your place at Mollage Media.
          </p>
          <button
            class="relative inline-flex items-center justify-center px-8 py-3.5 bg-white text-[#fe6600] rounded-xl hover:shadow-lg transition-all hover:scale-[1.02] group font-medium"
          >
            <span>View Open Positions</span>
             <span class="ml-3 inline-flex items-center justify-center">
              <Icon name="mdi:arrow-top-right" class="h-5 w-5" />
            </span>
          </button>
        </div>
      </section>

    </main>

    <!-- Footer (Reused from landing page for consistency) -->
  <LandingFooter />

   
  </div>
</template>

<script>
import { Icon } from "@iconify/vue";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
  name: "AboutUsPage",
  components: { Icon },
  data() {
    return {
      isMenuOpen: false,
    
      timeline: [
        { year: '2018', title: 'The Spark of an Idea', description: 'Mollage Media was founded in a small co-working space with a simple goal: to help great businesses tell their stories online.', icon: 'mdi:lightbulb-on-outline' },
        { year: '2020', title: 'Growth & Expansion', description: 'We celebrated our 50th client, moved into our first dedicated office, and expanded our services to include video production.', icon: 'mdi:rocket-launch-outline' },
        { year: '2022', title: 'Industry Recognition', description: 'Honored with the "Digital Agency of the Year" award and scaled our team to over 20 talented individuals.', icon: 'mdi:trophy-award' },
        { year: 'Today', title: 'Future-Focused', description: 'Continuously innovating with AI-driven analytics and expanding our global reach to serve clients worldwide.', icon: 'mdi:globe-model' },
      ],
      coreValues: [
        { title: 'Innovation', description: 'We constantly explore the new and are unafraid to challenge the status quo to find better ways to grow.', icon: 'mdi:brain' },
        { title: 'Partnership', description: 'We function as an extension of your team. Your success is the ultimate measure of our success.', icon: 'mdi:handshake-outline' },
        { title: 'Integrity', description: 'We believe in transparency and honesty. Our relationships are built on a foundation of trust.', icon: 'mdi:shield-check-outline' },
        { title: 'Excellence', description: 'We set a high bar for ourselves and our work, striving for exceptional results in everything we do.', icon: 'mdi:star-four-points-outline' },
      ],
       stats: [
        { value: "87%", label: "Client Growth Rate" },
        { value: "3.5x", label: "Average ROI" },
        { value: "500+", label: "Brands Helped" },
        { value: "98%", label: "Client Retention" },
      ],
      team: [ // Reused data from the landing page
        { name: "Alex Turner", position: "CEO & Founder", image: "https://images.unsplash.com/photo-1560250097-0b93528c311a?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=400&q=80&fit=max" },
        { name: "Jamie Smith", position: "Creative Director", image: "https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=400&q=80&fit=max" },
        { name: "Taylor Wong", position: "Digital Strategist", image: "https://images.unsplash.com/photo-1554151228-14d9def656e4?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=400&q=80&fit=max" },
        { name: "Morgan Lee", position: "Content Manager", image: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=400&q=80&fit=max" },
      ],
    };
  },
  mounted() {
    gsap.registerPlugin(ScrollTrigger);

    // Animate hero content on load
    gsap.from(".about-hero-content", { duration: 1, y: 50, ease: "power3.out" });

    // Animate mission section on scroll
    gsap.from(".mission-image", { scrollTrigger: { trigger: ".mission-image", start: "top 85%", toggleActions: "play none none none" }, duration: 1, x: -50, ease: "power3.out" });
    gsap.from(".mission-content", { scrollTrigger: { trigger: ".mission-content", start: "top 85%", toggleActions: "play none none none" }, duration: 1, x: 50, ease: "power3.out" });

    // Animate timeline items
    gsap.utils.toArray(".timeline-item").forEach((item, i) => {
      gsap.from(item, {
        scrollTrigger: {
          trigger: item,
          start: "top 85%",
          toggleActions: "play none none none",
        },
        y: 40,
        duration: 0.8,
        delay: i * 0.2,
        ease: "power3.out",
      });
    });

    // Animate value cards
    gsap.utils.toArray(".value-card").forEach((card, i) => {
      gsap.from(card, {
        scrollTrigger: { trigger: card, start: "top 85%", toggleActions: "play none none none" },
        y: 50,
        duration: 0.8,
        delay: i * 0.1,
        ease: "power3.out",
      });
    });
    
    // Animate team members (reused animation logic)
    gsap.utils.toArray(".team-member").forEach((member, i) => {
      gsap.from(member, {
        scrollTrigger: { trigger: member, start: "top 85%", toggleActions: "play none none none" },
        y: 30,
        duration: 0.6,
        delay: i * 0.1,
        ease: "back.out(1.2)",
      });
    });
  },
};
</script>

<style>
/* Reusing styles from the main landing page */
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap");

body {
  font-family: "Inter", sans-serif;
}

html {
  scroll-behavior: smooth;
}
</style>