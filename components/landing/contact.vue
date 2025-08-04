<template>
  <section id="contact" class="py-24 px-6 sm:px-8 lg:px-10 max-w-7xl mx-auto">
    <div class="grid lg:grid-cols-2 gap-16 items-center">
      <div>
        <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold mb-8">
          Let's
          <span
            class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent"
            >Connect</span
          >
        </h2>
        <p class="text-xl text-gray-600 mb-10 max-w-lg">
          Have a project in mind or want to learn more about our services? We'd
          love to hear from you.
        </p>
        <div class="space-y-6">
          <div class="flex items-start">
            <div class="bg-[#fff0e6] p-3 rounded-lg flex-shrink-0">
              <Icon name="mdi:phone-outline" class="h-6 w-6 text-[#fe6600]" />
            </div>
            <div class="ml-4">
              <h4 class="font-bold text-lg text-gray-900">Call Us</h4>
              <p class="text-gray-600">+1 (555) 123-4567</p>
            </div>
          </div>
          <div class="flex items-start">
            <div class="bg-[#fff0e6] p-3 rounded-lg flex-shrink-0">
              <Icon name="mdi:email-outline" class="h-6 w-6 text-[#fe6600]" />
            </div>
            <div class="ml-4">
              <h4 class="font-bold text-lg text-gray-900">Email Us</h4>
              <p class="text-gray-600">hello@mollagemedia.com</p>
            </div>
          </div>
          <div class="flex items-start">
            <div class="bg-[#fff0e6] p-3 rounded-lg flex-shrink-0">
              <Icon
                name="mdi:map-marker-outline"
                class="h-6 w-6 text-[#fe6600]"
              />
            </div>
            <div class="ml-4">
              <h4 class="font-bold text-lg text-gray-900">Visit Us</h4>
              <p class="text-gray-600">
                123 Marketing Ave, Suite 400<br />San Francisco, CA 94107
              </p>
            </div>
          </div>
        </div>
      </div>
      <div
        class="bg-white p-8 sm:p-10 rounded-2xl shadow-xl border border-gray-100"
      >
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
              for="service"
              class="block text-sm font-medium text-gray-700 mb-2"
              >Service Interest</label
            >
            <select
              id="service"
              v-model="form.service"
              class="w-full px-5 py-3.5 rounded-xl border border-gray-300 focus:ring-2 focus:ring-[#fe6600] focus:border-[#fe6600] transition-all appearance-none"
            >
              <option value="">Select a service</option>
              <option
                v-for="service in services"
                :key="service.title"
                :value="service.title"
              >
                {{ service.title }}
              </option>
            </select>
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
            class="w-full bg-gradient-to-r from-[#fe6600] to-[#541049] text-white px-8 py-4 rounded-xl hover:shadow-lg transition-all font-medium"
          >
            Send Message
          </button>
        </form>
      </div>
    </div>
  </section>
</template>

<script>
import { Icon } from "@iconify/vue";

export default {
  name: "Contact",
  components: { Icon },
  data() {
    return {
      form: {
        name: "",
        email: "",
        service: "",
        message: "",
      },
      services: [
        {
          title: "Digital Advertising",
        },
        {
          title: "SEO Optimization",
        },
        {
          title: "Content Creation",
        },
        {
          title: "Social Media",
        },
        {
          title: "Video Production",
        },
        {
          title: "Brand Strategy",
        },
      ],
    };
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
