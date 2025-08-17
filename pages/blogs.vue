<template>
  <div class="min-h-screen bg-white text-gray-900 font-sans antialiased">
    <!-- Gradient Background Elements -->
    <div class="fixed inset-0 overflow-hidden pointer-events-none">
      <div
        class="absolute top-0 right-0 w-96 h-96 bg-[#fe6600]/20 rounded-full mix-blend-multiply filter blur-3xl opacity-50"
      ></div>
      <div
        class="absolute top-2/3 left-0 w-96 h-96 bg-[#541049]/20 rounded-full mix-blend-multiply filter blur-3xl opacity-50"
      ></div>
    </div>

    <!-- Navigation (Consistent) -->
<LandingNav/>

    <main class="relative z-10">
      <!-- Blog Hero Section -->
      <section class="pt-40 pb-24 bg-gray-50/50">
        <div class="max-w-4xl mx-auto px-6 text-center blog-hero-content">
          <h1
            class="text-4xl md:text-5xl lg:text-6xl font-bold leading-tight tracking-tight mb-6"
          >
            Insights & Ideas From Our
            <span
              class="bg-gradient-to-r from-[#fe6600] to-[#541049] bg-clip-text text-transparent"
              >Marketing Experts</span
            >
          </h1>
          <p class="text-xl text-gray-600 max-w-3xl mx-auto mb-10">
            Stay ahead of the curve with the latest trends, strategies, and
            success stories in the world of digital marketing.
          </p>
          <div class="max-w-2xl mx-auto">
            <form @submit.prevent class="relative">
              <input
                type="search"
                v-model="searchQuery"
                placeholder="Search for articles..."
                class="w-full pl-6 pr-14 py-4 rounded-full border border-gray-200 focus:ring-2 focus:ring-[#fe6600] focus:border-[#fe6600] transition-all shadow-sm"
              />
              <button
                type="submit"
                class="absolute top-1/2 right-3 -translate-y-1/2 p-2.5 bg-[#fe6600] text-white rounded-full hover:bg-opacity-90"
              >
                <Icon name="mdi:magnify" class="h-5 w-5" />
              </button>
            </form>
          </div>
        </div>
      </section>

      <!-- Main Blog Content -->
      <div class="py-24 px-6 sm:px-8 lg:px-10">
        <div class="max-w-7xl mx-auto">
          <!-- Featured Post -->
          <section v-if="featuredPost" class="mb-24 featured-post-section">
            <h2 class="text-3xl font-bold mb-8 text-center">
              Featured Article
            </h2>
            <div
              class="grid lg:grid-cols-2 gap-10 items-center bg-gray-50 rounded-2xl p-8 border border-gray-100 shadow-lg"
            >
              <div class="rounded-xl overflow-hidden">
                <img
                  :src="featuredPost.image"
                  :alt="featuredPost.title"
                  class="w-full h-full object-cover"
                />
              </div>
              <div>
                <span
                  class="inline-block px-3 py-1 bg-[#fff8f2] text-[#fe6600] rounded-full text-sm font-medium mb-4"
                  >{{ featuredPost.category }}</span
                >
                <h3
                  class="text-3xl font-bold mb-4 hover:text-[#fe6600] transition-colors"
                >
                  <a href="#">{{ featuredPost.title }}</a>
                </h3>
                <p class="text-gray-600 mb-6">{{ featuredPost.excerpt }}</p>
                <div class="flex items-center">
                  <img
                    :src="featuredPost.author.avatar"
                    alt="author"
                    class="w-12 h-12 rounded-full mr-4"
                  />
                  <div>
                    <p class="font-semibold">{{ featuredPost.author.name }}</p>
                    <p class="text-sm text-gray-500">
                      {{ formatDate(featuredPost.date) }}
                    </p>
                  </div>
                </div>
              </div>
            </div>
          </section>

          <!-- Filter & Posts Grid -->
          <section>
            <!-- Filters -->
            <div class="flex flex-wrap justify-center gap-3 mb-12">
              <button
                v-for="cat in categories"
                :key="cat"
                @click="activeCategory = cat"
                :class="[
                  'px-5 py-2.5 rounded-full font-medium transition-colors text-sm',
                  activeCategory === cat
                    ? 'bg-[#fe6600] text-white shadow-md'
                    : 'bg-gray-100 text-gray-700 hover:bg-gray-200',
                ]"
              >
                {{ cat }}
              </button>
            </div>

            <!-- Posts Grid -->
            <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
              <div
                v-for="post in paginatedPosts"
                :key="post.id"
                class="blog-card bg-white rounded-2xl shadow-md overflow-hidden border border-gray-100 hover:shadow-xl hover:-translate-y-1 transition-all duration-300 flex flex-col"
              >
                <div class="h-56">
                  <img
                    :src="post.image"
                    :alt="post.title"
                    class="w-full h-full object-cover"
                  />
                </div>
                <div class="p-6 flex-grow flex flex-col">
                  <span
                    class="inline-block px-3 py-1 bg-[#fff8f2] text-[#fe6600] rounded-full text-xs font-medium mb-3 self-start"
                    >{{ post.category }}</span
                  >
                  <h3
                    class="text-xl font-bold mb-3 flex-grow hover:text-[#fe6600] transition-colors"
                  >
                    <a href="#">{{ post.title }}</a>
                  </h3>
                  <div
                    class="flex items-center mt-4 pt-4 border-t border-gray-100"
                  >
                    <img
                      :src="post.author.avatar"
                      alt="author"
                      class="w-10 h-10 rounded-full mr-3"
                    />
                    <div>
                      <p class="font-semibold text-sm">
                        {{ post.author.name }}
                      </p>
                      <p class="text-xs text-gray-500">
                        {{ formatDate(post.date) }}
                      </p>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <div v-if="filteredPosts.length === 0" class="text-center py-20">
              <Icon
                name="mdi:text-box-search-outline"
                class="h-16 w-16 text-gray-300 mx-auto mb-4"
              />
              <h3 class="text-2xl font-bold">No Articles Found</h3>
              <p class="text-gray-500 mt-2">
                Try adjusting your search or filter criteria.
              </p>
            </div>

            <!-- Pagination -->
            <div
              v-if="totalPages > 1"
              class="flex justify-center items-center gap-4 mt-16"
            >
              <button
                @click="prevPage"
                :disabled="currentPage === 1"
                class="px-4 py-2 rounded-lg border border-gray-300 bg-white hover:bg-gray-100 disabled:opacity-50 disabled:cursor-not-allowed"
              >
                Previous
              </button>
              <span class="text-gray-700 font-medium"
                >Page {{ currentPage }} of {{ totalPages }}</span
              >
              <button
                @click="nextPage"
                :disabled="currentPage === totalPages"
                class="px-4 py-2 rounded-lg border border-gray-300 bg-white hover:bg-gray-100 disabled:opacity-50 disabled:cursor-not-allowed"
              >
                Next
              </button>
            </div>
          </section>
        </div>
      </div>

      <!-- Newsletter CTA -->
      <section class="py-24 bg-gradient-to-r from-[#fe6600] to-[#541049]">
        <div class="max-w-3xl mx-auto px-6 text-center">
          <h2 class="text-3xl md:text-4xl font-bold text-white mb-6">
            Never Miss an Insight
          </h2>
          <p class="text-xl text-white/80 mb-10">
            Subscribe to our newsletter and get the latest articles, case
            studies, and marketing tips delivered straight to your inbox.
          </p>
          <form class="flex flex-col sm:flex-row gap-4 max-w-xl mx-auto">
            <input
              type="email"
              placeholder="Enter your email"
              class="w-full px-5 py-4 rounded-lg focus:outline-none text-gray-900 flex-grow"
            />
            <button
              type="submit"
              class="bg-white text-[#fe6600] px-8 py-4 rounded-lg font-bold hover:bg-gray-200 transition-colors"
            >
              Subscribe
            </button>
          </form>
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
  name: "BlogPage",
  components: { Icon },
  data() {
    return {
      isMenuOpen: false,
      searchQuery: "",
      activeCategory: "All",
      currentPage: 1,
      postsPerPage: 6,
   
      blogPosts: [
        {
          id: 1,
          title: "The Future of SEO: 5 Trends to Watch in 2024",
          category: "SEO",
          image:
            "https://images.unsplash.com/photo-1551288049-bebda4e38f71?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
          excerpt:
            "AI, voice search, and visual search are reshaping the SEO landscape. Here's how to prepare your strategy for what's next.",
          author: {
            name: "Alex Turner",
            avatar:
              "https://images.unsplash.com/photo-1560250097-0b93528c311a?ixlib=rb-1.2.1&auto=format&fit=crop&w=100&h=100&q=80",
          },
          date: "2023-10-26",
          featured: true,
        },
        {
          id: 2,
          title:
            "From Clicks to Customers: A Guide to Conversion Rate Optimization",
          category: "Marketing",
          image:
            "https://images.unsplash.com/photo-1556740738-b6a63e27c4df?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
          excerpt:
            "Turning website visitors into loyal customers requires more than just traffic. Dive into the art and science of CRO.",
          author: {
            name: "Taylor Wong",
            avatar:
              "https://images.unsplash.com/photo-1554151228-14d9def656e4?ixlib=rb-1.2.1&auto=format&fit=crop&w=100&h=100&q=80",
          },
          date: "2023-10-22",
        },
        {
          id: 3,
          title:
            "Storytelling in Branding: How to Create a Narrative That Sells",
          category: "Branding",
          image:
            "https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
          excerpt:
            "Discover how to weave compelling stories into your brand identity to build deeper connections with your audience.",
          author: {
            name: "Morgan Lee",
            avatar:
              "https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&auto=format&fit=crop&w=100&h=100&q=80",
          },
          date: "2023-10-18",
        },
        {
          id: 4,
          title:
            "The Power of Visuals: Elevating Your Content with Great Design",
          category: "Design",
          image:
            "https://images.unsplash.com/photo-1572044162444-24c95621ec3b?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
          excerpt:
            "In a sea of content, striking visuals are your best friend. Learn design principles that make your brand stand out.",
          author: {
            name: "Jamie Smith",
            avatar:
              "https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?ixlib=rb-1.2.1&auto=format&fit=crop&w=100&h=100&q=80",
          },
          date: "2023-10-15",
        },
        {
          id: 5,
          title: "Mastering Google Ads: A Beginner's Guide to PPC Success",
          category: "Marketing",
          image:
            "https://images.unsplash.com/photo-1599690987392-291075a0551e?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
          excerpt:
            "Launch your first successful PPC campaign with this step-by-step guide to Google Ads, from keywords to ad copy.",
          author: {
            name: "Taylor Wong",
            avatar:
              "https://images.unsplash.com/photo-1554151228-14d9def656e4?ixlib=rb-1.2.1&auto=format&fit=crop&w=100&h=100&q=80",
          },
          date: "2023-10-10",
        },
        {
          id: 6,
          title: "How to Conduct a Content Audit That Drives Real Results",
          category: "SEO",
          image:
            "https://images.unsplash.com/photo-1516321497487-e288fb19713f?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
          excerpt:
            "Unlock hidden potential in your existing content. Learn how to audit, prune, and update your way to better rankings.",
          author: {
            name: "Alex Turner",
            avatar:
              "https://images.unsplash.com/photo-1560250097-0b93528c311a?ixlib=rb-1.2.1&auto=format&fit=crop&w=100&h=100&q=80",
          },
          date: "2023-10-05",
        },
        {
          id: 7,
          title: "The Psychology of Color in Marketing and Branding",
          category: "Branding",
          image:
            "https://images.unsplash.com/photo-1522881451255-f59ad836fdfb?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
          excerpt:
            "Colors evoke emotions and influence decisions. Learn how to choose a color palette that resonates with your target audience.",
          author: {
            name: "Jamie Smith",
            avatar:
              "https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?ixlib=rb-1.2.1&auto=format&fit=crop&w=100&h=100&q=80",
          },
          date: "2023-10-01",
        },
      ],
    };
  },
  computed: {
    featuredPost() {
      return this.blogPosts.find((p) => p.featured);
    },
    categories() {
      const cats = this.blogPosts.map((p) => p.category);
      return ["All", ...new Set(cats)];
    },
    filteredPosts() {
      let posts = this.blogPosts.filter((p) => !p.featured);

      if (this.activeCategory !== "All") {
        posts = posts.filter((p) => p.category === this.activeCategory);
      }

      if (this.searchQuery.trim() !== "") {
        const query = this.searchQuery.toLowerCase();
        posts = posts.filter(
          (p) =>
            p.title.toLowerCase().includes(query) ||
            p.excerpt.toLowerCase().includes(query)
        );
      }

      return posts;
    },
    totalPages() {
      return Math.ceil(this.filteredPosts.length / this.postsPerPage);
    },
    paginatedPosts() {
      const start = (this.currentPage - 1) * this.postsPerPage;
      const end = start + this.postsPerPage;
      return this.filteredPosts.slice(start, end);
    },
  },
  watch: {
    activeCategory() {
      this.currentPage = 1;
    },
    searchQuery() {
      this.currentPage = 1;
    },
  },
  methods: {
    formatDate(dateString) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(dateString).toLocaleDateString("en-US", options);
    },
    nextPage() {
      if (this.currentPage < this.totalPages) {
        this.currentPage++;
      }
    },
    prevPage() {
      if (this.currentPage > 1) {
        this.currentPage--;
      }
    },
  },
  mounted() {
    gsap.registerPlugin(ScrollTrigger);
    gsap.from(".blog-hero-content", {
      duration: 1,
      y: 50,
      ease: "power3.out",
    });
    gsap.from(".featured-post-section", {
      scrollTrigger: { trigger: ".featured-post-section", start: "top 80%" },
      duration: 1,
      y: 50,
      ease: "power3.out",
    });
    ScrollTrigger.batch(".blog-card", {
      onEnter: (batch) =>
        gsap.from(batch, {
          y: 50,
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
</style>
