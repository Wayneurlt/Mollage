<template>
  <div class="min-h-screen bg-gray-50 text-gray-900 font-sans antialiased">
    <!-- Gradient Background Elements -->
    <div class="fixed inset-0 overflow-hidden pointer-events-none">
      <div
        class="absolute top-0 left-1/4 w-96 h-96 bg-[#fe6600] rounded-full mix-blend-multiply filter blur-3xl opacity-15"
      ></div>
      <div
        class="absolute bottom-0 right-1/4 w-96 h-96 bg-[#541049] rounded-full mix-blend-multiply filter blur-3xl opacity-15"
      ></div>
    </div>

    <!-- Navigation (Consistent with other pages) -->
  <LandingNav/>

    <main class="relative z-10">
      <!-- Careers Hero Section -->
      <section class="pt-40 pb-24 text-center bg-white/50">
        <div class="max-w-4xl mx-auto px-6 careers-hero-content">
          <span
            class="inline-block px-4 py-2 bg-[#fff8f2] rounded-full text-[#fe6600] font-medium mb-4"
            >Join Our Mission</span
          >
          <h1
            class="text-4xl md:text-5xl lg:text-6xl font-bold leading-tight tracking-tight mb-6"
          >
            Help Us Build the Future of
            <span
              class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent"
              >Digital Marketing</span
            >
          </h1>
          <p class="text-xl text-gray-600 max-w-3xl mx-auto">
            We're a passionate, results-driven team looking for creative minds
            and strategic thinkers to help us redefine what's possible for our
            clients. Ready to make an impact?
          </p>
        </div>
      </section>

      <!-- Perks & Benefits Section -->
      <section class="py-24 px-6 sm:px-8 lg:px-10">
        <div class="max-w-7xl mx-auto">
          <div class="text-center mb-20">
            <h2 class="text-3xl md:text-4xl font-bold">
              Why You'll Love Working Here
            </h2>
            <p class="max-w-2xl mx-auto text-xl text-gray-600 mt-4">
              We invest in our people and culture to create an environment where
              everyone can thrive.
            </p>
          </div>
          <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
            <div
              v-for="perk in perks"
              :key="perk.title"
              class="perk-card bg-white p-8 rounded-2xl shadow-sm border border-gray-100 text-center hover:shadow-lg transition-shadow"
            >
              <div
                class="inline-block p-5 bg-gradient-to-br from-[#fff0e6] to-[#f3e8f1] rounded-2xl mb-6"
              >
                <Icon :name="perk.icon" class="h-10 w-10 text-[#fe6600]" />
              </div>
              <h3 class="text-xl font-bold mb-3">{{ perk.title }}</h3>
              <p class="text-gray-600">{{ perk.description }}</p>
            </div>
          </div>
        </div>
      </section>

      <!-- Open Positions Section -->
      <section id="openings" class="py-24 bg-white px-6 sm:px-8 lg:px-10">
        <div class="max-w-5xl mx-auto">
          <div class="text-center mb-16">
            <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold mb-6">
              Find Your
              <span
                class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent"
                >Next Role</span
              >
            </h2>
            <p class="max-w-2xl mx-auto text-xl text-gray-600">
              Explore our current openings. We're excited to learn how your
              skills and passion can contribute to our team.
            </p>
          </div>

          <!-- Job Filters -->
          <div class="flex flex-wrap justify-center gap-3 mb-12">
            <button
              v-for="department in [
                'All',
                'Marketing',
                'Design',
                'Engineering',
                'Sales',
              ]"
              :key="department"
              @click="activeFilter = department"
              :class="[
                'px-5 py-2.5 rounded-full font-medium transition-colors text-sm',
                activeFilter === department
                  ? 'bg-[#fe6600] text-white shadow-md'
                  : 'bg-gray-100 text-gray-700 hover:bg-gray-200',
              ]"
            >
              {{ department }}
            </button>
          </div>

          <!-- Job Listings -->
          <div class="space-y-4">
            <div
              v-for="job in filteredJobs"
              :key="job.id"
              class="job-listing bg-gray-50 border border-gray-100 rounded-xl overflow-hidden transition-all duration-300"
            >
              <button
                @click="toggleAccordion(job.id)"
                class="w-full text-left p-6 flex justify-between items-center hover:bg-gray-100"
              >
                <div>
                  <h3 class="text-xl font-bold text-gray-900">
                    {{ job.title }}
                  </h3>
                  <p class="text-gray-600 mt-1">
                    {{ job.location }} · {{ job.type }}
                  </p>
                </div>
                <Icon
                  name="mdi:chevron-down"
                  class="h-6 w-6 text-gray-500 transition-transform duration-300"
                  :class="{ 'rotate-180': openAccordion === job.id }"
                />
              </button>
              <transition name="accordion">
                <div v-if="openAccordion === job.id" class="px-6 pb-8">
                  <div class="border-t border-gray-200 pt-6">
                    <p class="text-gray-700 mb-6">{{ job.description }}</p>
                    <h4 class="font-bold text-lg mb-3">
                      Key Responsibilities:
                    </h4>
                    <ul
                      class="list-disc list-inside space-y-2 text-gray-600 mb-6"
                    >
                      <li v-for="item in job.responsibilities" :key="item">
                        {{ item }}
                      </li>
                    </ul>
                    <h4 class="font-bold text-lg mb-3">Qualifications:</h4>
                    <ul
                      class="list-disc list-inside space-y-2 text-gray-600 mb-6"
                    >
                      <li v-for="item in job.qualifications" :key="item">
                        {{ item }}
                      </li>
                    </ul>
                    <button
                      class="inline-flex items-center px-6 py-3 bg-gradient-to-r from-[#fe6600] to-[#541049] text-white rounded-lg hover:shadow-lg transition-all hover:scale-[1.02]"
                    >
                      Apply Now
                      <Icon name="mdi:arrow-right" class="ml-2 h-5 w-5" />
                    </button>
                  </div>
                </div>
              </transition>
            </div>
            <div v-if="filteredJobs.length === 0" class="text-center py-12">
              <Icon
                name="mdi:emoticon-sad-outline"
                class="h-12 w-12 text-gray-400 mx-auto mb-4"
              />
              <h3 class="text-xl font-bold">
                No Openings in {{ activeFilter }}
              </h3>
              <p class="text-gray-500 mt-2">
                Check back soon or view other departments!
              </p>
            </div>
          </div>
        </div>
      </section>

      <!-- Culture Gallery Section -->
      <section class="py-24 px-6 sm:px-8 lg:px-10">
        <div class="max-w-7xl mx-auto">
          <div class="text-center mb-20">
            <h2 class="text-3xl md:text-4xl font-bold">
              A Glimpse Into
              <span
                class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent"
                >Our Culture</span
              >
            </h2>
            <p class="max-w-2xl mx-auto text-xl text-gray-600 mt-4">
              We're collaborative, innovative, and we have fun doing it.
            </p>
          </div>
          <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
            <div
              v-for="(img, i) in galleryImages"
              :key="i"
              class="gallery-item group overflow-hidden rounded-2xl"
              :class="i === 0 || i === 3 ? 'md:col-span-2' : ''"
            >
              <img
                :src="img"
                alt="Mollage Media team and office"
                class="h-full w-full object-cover transition-transform duration-500 group-hover:scale-105"
              />
            </div>
          </div>
        </div>
      </section>

      <!-- Spontaneous Application CTA -->
      <section class="py-24 bg-gradient-to-r from-[#541049] to-[#3a0b34]">
        <div class="max-w-4xl mx-auto px-6 text-center">
          <h2 class="text-3xl md:text-4xl font-bold text-white mb-6">
            Don't See the Perfect Fit?
          </h2>
          <p class="text-xl text-gray-300 mb-10 max-w-2xl mx-auto">
            We're always on the lookout for exceptional talent. If you believe
            you have what it takes to make a difference at Mollage Media, send
            us your resume.
          </p>
          <button
            class="relative inline-flex items-center justify-center px-8 py-3.5 bg-white text-[#fe6600] rounded-xl hover:shadow-lg transition-all hover:scale-[1.02] group font-medium"
          >
            <span>Submit Your Resume</span>
            <span class="ml-3 inline-flex items-center justify-center">
              <Icon name="mdi:email-fast-outline" class="h-5 w-5" />
            </span>
          </button>
        </div>
      </section>
    </main>
    <!-- Footer (Consistent) -->
  <LandingFooter />

  
  </div>
</template>

<script>
import { LandingFooter } from "#components";
import { Icon } from "@iconify/vue";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
  name: "CareersPage",
  components: { Icon },
  data() {
    return {
      isMenuOpen: false,
      activeFilter: "All",
      openAccordion: null,
    
      perks: [
        {
          title: "Flexible Work",
          description:
            "Balance your life and work with flexible hours and remote work options.",
          icon: "mdi:clock-time-eight-outline",
        },
        {
          title: "Health & Wellness",
          description:
            "Comprehensive health, dental, and vision insurance for you and your family.",
          icon: "mdi:heart-pulse",
        },
        {
          title: "Professional Growth",
          description:
            "An annual budget for courses, conferences, and books to fuel your development.",
          icon: "mdi:school-outline",
        },
        {
          title: "Generous PTO",
          description:
            "Recharge with a generous paid time off policy and company-wide holidays.",
          icon: "mdi:beach",
        },
      ],
      galleryImages: [
        "https://images.unsplash.com/photo-1522202176988-66273c2fd55f?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80",
        "https://images.unsplash.com/photo-1552664730-d307ca884978?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
        "https://images.unsplash.com/photo-1542744173-8e7e53415bb0?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
        "https://images.unsplash.com/photo-1523240795612-9a054b0db644?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80",
      ],
      jobOpenings: [
        {
          id: 1,
          title: "Senior SEO Strategist",
          department: "Marketing",
          location: "Remote",
          type: "Full-Time",
          description:
            "Lead our SEO initiatives, developing and executing strategies to dramatically increase organic traffic and search visibility for our diverse portfolio of clients.",
          responsibilities: [
            "Develop and execute successful SEO strategies",
            "Conduct keyword research to guide content teams",
            "Monitor daily performance metrics to understand SEO strategy performance",
          ],
          qualifications: [
            "5+ years of experience in SEO",
            "Proven track record of successful SEO campaigns",
            "Expertise with SEO tools (Ahrefs, SEMrush, etc.)",
          ],
        },
        {
          id: 2,
          title: "UI/UX Designer",
          department: "Design",
          location: "San Francisco, CA",
          type: "Full-Time",
          description:
            "Create intuitive, engaging, and beautiful user experiences across a variety of web and mobile projects. You will own the design process from wireframes to high-fidelity mockups.",
          responsibilities: [
            "Create user flows, wireframes, prototypes, and mockups",
            "Design UI elements such as input controls, navigational components and informational components",
            "Identify and troubleshoot UX problems",
          ],
          qualifications: [
            "3+ years of UI/UX design experience",
            "Strong portfolio of design projects",
            "Proficiency in Figma, Sketch, or Adobe XD",
          ],
        },
        {
          id: 3,
          title: "Full-Stack Engineer",
          department: "Engineering",
          location: "Remote",
          type: "Full-Time",
          description:
            "Build and maintain scalable, high-performance web applications. You will work on both front-end and back-end development, contributing to all phases of the development lifecycle.",
          responsibilities: [
            "Design, build, and maintain efficient, reusable, and reliable code",
            "Integrate data from various back-end services and databases",
            "Ensure the best possible performance, quality, and responsiveness of applications",
          ],
          qualifications: [
            "4+ years of experience with Vue.js/React and Node.js",
            "Experience with cloud services (AWS, Google Cloud)",
            "Strong understanding of RESTful APIs",
          ],
        },
        {
          id: 4,
          title: "Account Executive",
          department: "Sales",
          location: "New York, NY",
          type: "Full-Time",
          description:
            "Drive our business growth by building and maintaining strong client relationships. You will be responsible for the full sales cycle, from prospecting to closing deals.",
          responsibilities: [
            "Identify and prospect new sales leads",
            "Develop and deliver compelling sales presentations",
            "Negotiate contracts and close agreements",
          ],
          qualifications: [
            "3+ years of experience in B2B sales, preferably in a marketing agency",
            "Excellent communication and negotiation skills",
            "Proven ability to meet and exceed sales quotas",
          ],
        },
      ],
    };
  },
  computed: {
    filteredJobs() {
      if (this.activeFilter === "All") {
        return this.jobOpenings;
      }
      return this.jobOpenings.filter(
        (job) => job.department === this.activeFilter
      );
    },
  },
  methods: {
    toggleAccordion(id) {
      this.openAccordion = this.openAccordion === id ? null : id;
    },
  },
  mounted() {
    gsap.registerPlugin(ScrollTrigger);

    gsap.from(".careers-hero-content", {
      duration: 1,
      y: 50,
      opacity: 0,
      delay: 0.2,
      ease: "power3.out",
    });

    gsap.utils.toArray(".perk-card").forEach((card, i) => {
      gsap.from(card, {
        scrollTrigger: {
          trigger: card,
          start: "top 85%",
          toggleActions: "play none none none",
        },
        y: 40,
        opacity: 0,
        duration: 0.8,
        delay: i * 0.1,
        ease: "power3.out",
      });
    });

    gsap.utils.toArray(".gallery-item").forEach((item, i) => {
      gsap.from(item, {
        scrollTrigger: {
          trigger: item,
          start: "top 90%",
          toggleActions: "play none none none",
        },
        scale: 0.9,
        opacity: 0,
        duration: 0.8,
        delay: i * 0.1,
        ease: "power3.out",
      });
    });
  },
};
</script>

<style>
/* Reusing global styles */
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap");
body {
  font-family: "Inter", sans-serif;
}
html {
  scroll-behavior: smooth;
}

/* Accordion transition */
.accordion-enter-active,
.accordion-leave-active {
  transition: all 0.4s ease-in-out;
  max-height: 500px;
  opacity: 1;
}
.accordion-enter-from,
.accordion-leave-to {
  max-height: 0;
  opacity: 0;
  padding-top: 0;
  padding-bottom: 0;
  margin-top: -1rem; /* Smooth out collapse */
}
</style>
