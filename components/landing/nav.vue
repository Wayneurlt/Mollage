<template>
  <nav class="fixed w-full bg-white z-50 shadow-sm">
    <div class="max-w-7xl mx-auto px-6 py-4">
      <div class="flex justify-between items-center">
        <div class="flex items-center space-x-2">
          <NuxtLink to="/">
            <img
              src="/assets/images/logo.png"
              alt="Mollage Media Logo"
              class="h-20 w-auto"
            />
          </NuxtLink>
        </div>

        <div class="hidden lg:flex items-center space-x-8">
          <a
            v-for="item in navItems"
            :key="item.name"
            :href="item.href"
            class="text-gray-700 hover:text-[#fe6600] transition-colors font-medium relative group"
          >
            {{ item.name }}
            <span
              class="absolute bottom-0 left-0 w-0 h-0.5 bg-[#fe6600] transition-all duration-300 group-hover:w-full"
            ></span>
          </a>
          <button
            class="relative inline-flex items-center px-6 py-2.5 bg-gradient-to-r from-[#fe6600] to-[#541049] text-white rounded-lg hover:shadow-lg transition-all hover:scale-[1.02]"
          >
            <span>Get Started</span>
            <span class="ml-2 inline-flex items-center justify-center">
              <Icon name="mdi:arrow-right" class="h-5 w-5" />
            </span>
          </button>
        </div>
        <button
          @click="isMenuOpen = !isMenuOpen"
          class="lg:hidden text-gray-700 p-2 rounded-lg hover:bg-gray-100"
        >
          <Icon :name="isMenuOpen ? 'mdi:close' : 'mdi:menu'" class="h-6 w-6" />
        </button>
      </div>
    </div>

    <!-- Mobile menu -->
    <transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="transform scale-95 opacity-0"
      enter-to-class="transform scale-100 opacity-100"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="transform scale-100 opacity-100"
      leave-to-class="transform scale-95 opacity-0"
    >
      <div
        v-if="isMenuOpen"
        class="lg:hidden bg-white py-4 px-6 shadow-lg border-t border-gray-100"
      >
        <div class="flex flex-col space-y-4">
          <a
            v-for="item in navItems"
            :key="item.name"
            :href="item.href"
            class="text-gray-700 hover:text-[#fe6600] transition-colors font-medium py-2 border-b border-gray-100"
          >
            {{ item.name }}
          </a>
          <a
            href="/contact"
            class="w-full mt-4 inline-flex items-center justify-center px-6 py-2.5 bg-gradient-to-r from-[#fe6600] to-[#541049] text-white rounded-lg hover:shadow-lg"
            >Get Started</a
          >
        </div>
      </div>
    </transition>
  </nav>
</template>

<script>
import { Icon } from "@iconify/vue";

export default {
  name: "Navbar",
  components: { Icon },
  data() {
    return {
      isMenuOpen: false,
      navItems: [
        { name: "Home", href: "#home" },
        { name: "Services", href: "#services" },
        { name: "Work", href: "#portfolio" },
        { name: "About", href: "#about" },
        { name: "Contact", href: "#contact" },
      ],
    };
  },
};
</script>
