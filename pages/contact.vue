<template>
  <div class="min-h-screen bg-gray-50 text-gray-900 font-sans antialiased">
    <!-- Gradient Background Elements -->
    <div class="fixed inset-0 overflow-hidden pointer-events-none">
      <div
        class="absolute -top-20 right-0 w-96 h-96 bg-[#fe6600]/20 rounded-full mix-blend-multiply filter blur-3xl opacity-50"
      ></div>
      <div
        class="absolute top-1/2 left-0 w-96 h-96 bg-[#541049]/20 rounded-full mix-blend-multiply filter blur-3xl opacity-50"
      ></div>
    </div>

    <!-- Navigation (Consistent) -->
     <LandingNav />

    <main class="relative z-10">
      <!-- Contact Hero Section -->
      <section class="pt-40 pb-24 text-center">
        <div class="max-w-4xl mx-auto px-6 contact-hero-content">
          <h1
            class="text-4xl md:text-5xl lg:text-6xl font-bold leading-tight tracking-tight mb-6"
          >
            Let's Start a
            <span
              class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent"
              >Conversation</span
            >
          </h1>
          <p class="text-xl text-gray-600 max-w-3xl mx-auto">
            Whether you have a question about our services, a project proposal,
            or just want to say hello, we'd love to hear from you.
          </p>
        </div>
      </section>

      <!-- Contact Info & Form Section -->
      <section class="py-24 bg-white/70 px-6 sm:px-8 lg:px-10">
        <div class="max-w-7xl mx-auto grid lg:grid-cols-2 gap-16 items-start">
          <!-- Contact Info -->
          <div class="contact-info-content">
            <h2 class="text-3xl font-bold mb-8">Get in Touch</h2>
            <p class="text-lg text-gray-600 mb-12">
              Use the form to send us a message, or reach out directly through
              one of the channels below. We aim to respond to all inquiries
              within 24 hours.
            </p>
            <div class="space-y-8">
              <div class="flex items-start">
                <div
                  class="flex-shrink-0 p-4 bg-gradient-to-br from-[#fff0e6] to-[#f3e8f1] rounded-2xl"
                >
                  <Icon
                    name="mdi:email-outline"
                    class="h-8 w-8 text-[#fe6600]"
                  />
                </div>
                <div class="ml-5">
                  <h3 class="text-xl font-bold">Email Us</h3>
                  <p class="text-gray-600 mt-1">
                    Send your project details or questions to our team.
                  </p>
                  <a
                    href="mailto:hello@mollagemedia.com"
                    class="text-[#fe6600] font-medium mt-2 inline-block hover:underline"
                    >hello@mollagemedia.com</a
                  >
                </div>
              </div>
              <div class="flex items-start">
                <div
                  class="flex-shrink-0 p-4 bg-gradient-to-br from-[#fff0e6] to-[#f3e8f1] rounded-2xl"
                >
                  <Icon
                    name="mdi:phone-outline"
                    class="h-8 w-8 text-[#fe6600]"
                  />
                </div>
                <div class="ml-5">
                  <h3 class="text-xl font-bold">Call Us</h3>
                  <p class="text-gray-600 mt-1">
                    Speak directly with a member of our team.
                  </p>
                  <a
                    href="tel:+15551234567"
                    class="text-[#fe6600] font-medium mt-2 inline-block hover:underline"
                    >+1 (555) 123-4567</a
                  >
                </div>
              </div>
              <div class="flex items-start">
                <div
                  class="flex-shrink-0 p-4 bg-gradient-to-br from-[#fff0e6] to-[#f3e8f1] rounded-2xl"
                >
                  <Icon
                    name="mdi:map-marker-outline"
                    class="h-8 w-8 text-[#fe6600]"
                  />
                </div>
                <div class="ml-5">
                  <h3 class="text-xl font-bold">Visit Us</h3>
                  <p class="text-gray-600 mt-1">
                    Schedule a meeting at our main office.
                  </p>
                  <p class="font-medium mt-2">
                    123 Marketing Ave, Suite 400<br />San Francisco, CA 94107
                  </p>
                </div>
              </div>
            </div>
          </div>

          <!-- Contact Form -->
          <div
            class="bg-white p-8 sm:p-10 rounded-2xl shadow-2xl border border-gray-100 contact-form-wrapper"
          >
            <h2 class="text-2xl font-bold mb-6 text-center">
              Send Us a Message
            </h2>
            <form @submit.prevent="submitForm" class="space-y-6">
              <div>
                <label
                  for="name"
                  class="block text-sm font-medium text-gray-700 mb-2"
                  >Full Name</label
                >
                <input
                  type="text"
                  id="name"
                  v-model="form.name"
                  required
                  class="w-full px-5 py-3.5 rounded-xl border border-gray-300 focus:ring-2 focus:ring-[#fe6600] focus:border-[#fe6600] transition-all"
                />
              </div>
              <div>
                <label
                  for="email"
                  class="block text-sm font-medium text-gray-700 mb-2"
                  >Email Address</label
                >
                <input
                  type="email"
                  id="email"
                  v-model="form.email"
                  required
                  class="w-full px-5 py-3.5 rounded-xl border border-gray-300 focus:ring-2 focus:ring-[#fe6600] focus:border-[#fe6600] transition-all"
                />
              </div>
              <div>
                <label
                  for="subject"
                  class="block text-sm font-medium text-gray-700 mb-2"
                  >Subject</label
                >
                <input
                  type="text"
                  id="subject"
                  v-model="form.subject"
                  required
                  class="w-full px-5 py-3.5 rounded-xl border border-gray-300 focus:ring-2 focus:ring-[#fe6600] focus:border-[#fe6600] transition-all"
                />
              </div>
              <div>
                <label
                  for="message"
                  class="block text-sm font-medium text-gray-700 mb-2"
                  >Your Message</label
                >
                <textarea
                  id="message"
                  v-model="form.message"
                  rows="5"
                  class="w-full px-5 py-3.5 rounded-xl border border-gray-300 focus:ring-2 focus:ring-[#fe6600] focus:border-[#fe6600] transition-all"
                ></textarea>
              </div>
              <button
                type="submit"
                class="w-full bg-gradient-to-r from-[#fe6600] to-[#541049] text-white px-8 py-4 rounded-xl hover:shadow-lg transition-all font-medium text-lg"
              >
                Send Message
              </button>
            </form>
          </div>
        </div>
      </section>

      <!-- Map Section -->
      <section class="map-section">
        <!-- Replace the src with your actual Google Maps embed link -->
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3153.297448689531!2d-122.3986214241913!3d37.78369697198224!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x80858064a18d1033%3A0x86749035c9e172a6!2s123%20Marketing%20Ave%2C%20San%20Francisco%2C%20CA%2094107%2C%20USA!5e0!3m2!1sen!2suk!4v1678886543210!5m2!1sen!2suk"
          width="100%"
          height="500"
          style="border: 0"
          allowfullscreen=""
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
          class="grayscale hover:grayscale-0 transition-all duration-500"
        >
        </iframe>
      </section>

      <!-- FAQ Section -->
      <section class="py-24 px-6 sm:px-8 lg:px-10">
        <div class="max-w-4xl mx-auto">
          <div class="text-center mb-16">
            <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold mb-6">
              Frequently Asked
              <span
                class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent"
                >Questions</span
              >
            </h2>
            <p class="max-w-2xl mx-auto text-xl text-gray-600">
              Have questions? We have answers. Check out our FAQ section below.
            </p>
          </div>
          <div class="space-y-4">
            <div
              v-for="(faq, index) in faqs"
              :key="index"
              class="faq-item bg-white border border-gray-100 rounded-xl overflow-hidden shadow-sm"
            >
              <button
                @click="toggleFaq(index)"
                class="w-full text-left p-6 flex justify-between items-center hover:bg-gray-50 transition-colors"
              >
                <h3 class="text-lg font-semibold">{{ faq.question }}</h3>
                <Icon
                  name="mdi:chevron-down"
                  class="h-6 w-6 text-gray-500 transition-transform duration-300"
                  :class="{ 'rotate-180 text-[#fe6600]': openFaq === index }"
                />
              </button>
              <transition name="faq-accordion">
                <div v-if="openFaq === index" class="px-6 pb-6">
                  <div class="border-t border-gray-200 pt-4">
                    <p class="text-gray-700 leading-relaxed">
                      {{ faq.answer }}
                    </p>
                  </div>
                </div>
              </transition>
            </div>
          </div>
        </div>
      </section>
    </main>
    <!-- Footer (Consistent) -->
    <LandingFooter />
  </div>
</template>

<script>
import { Icon } from "@iconify/vue";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
  name: "ContactPage",
  components: { Icon },
  data() {
    return {
      isMenuOpen: false,
      openFaq: null,

      form: {
        name: "",
        email: "",
        subject: "",
        message: "",
      },
      faqs: [
        {
          question: "What types of industries do you specialize in?",
          answer:
            "We have extensive experience across a wide range of industries, including tech, e-commerce, healthcare, and B2B services. Our strategies are always tailored to the unique challenges and opportunities of your specific market.",
        },
        {
          question:
            "How long does it take to see results from an SEO campaign?",
          answer:
            "While some on-page optimizations can yield quick improvements, significant results from SEO typically take 3-6 months. SEO is a long-term strategy that builds sustainable growth over time.",
        },
        {
          question: "What is your pricing model?",
          answer:
            "Our pricing is customized based on the scope of the project, the services required, and your specific goals. We offer both project-based pricing and monthly retainers. Contact us for a detailed proposal.",
        },
        {
          question: "Can you work with small businesses and startups?",
          answer:
            "Absolutely! We love working with businesses of all sizes. We offer scalable solutions that can grow with you, ensuring you get the best return on your investment, no matter your budget.",
        },
      ],
    };
  },
  methods: {
    submitForm() {
      console.log("Contact form submitted:", this.form);
      alert("Thank you for your message! We will get back to you shortly.");
      this.form = { name: "", email: "", subject: "", message: "" };
    },
    toggleFaq(index) {
      this.openFaq = this.openFaq === index ? null : index;
    },
  },
  mounted() {
    gsap.registerPlugin(ScrollTrigger);

    gsap.from(".contact-hero-content", {
      duration: 1,
      y: 50,
      ease: "power3.out",
    });
    gsap.from(".contact-info-content", {
      scrollTrigger: { trigger: ".contact-info-content", start: "top 85%" },
      duration: 1,
      x: -50,
      ease: "power3.out",
    });
    gsap.from(".contact-form-wrapper", {
      scrollTrigger: { trigger: ".contact-form-wrapper", start: "top 85%" },
      duration: 1,
      x: 50,
      ease: "power3.out",
    });
    gsap.from(".map-section", {
      scrollTrigger: { trigger: ".map-section", start: "top 90%" },
      duration: 1.2,
      y: 50,
      ease: "power3.out",
    });

    ScrollTrigger.batch(".faq-item", {
      onEnter: (batch) =>
        gsap.from(batch, {
          y: 30,
          stagger: 0.1,
          ease: "power3.out",
        }),
      start: "top 90%",
      once: true,
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

/* FAQ Accordion transition */
.faq-accordion-enter-active,
.faq-accordion-leave-active {
  transition: all 0.4s ease-in-out;
  max-height: 200px;
  opacity: 1;
}
.faq-accordion-enter-from,
.faq-accordion-leave-to {
  max-height: 0;
  opacity: 0;
}
</style>
