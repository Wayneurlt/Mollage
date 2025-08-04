<template>
  <div class="min-h-screen bg-white text-gray-900 font-sans antialiased">
    <!-- Gradient Background Elements (subtler for this page) -->
    <div class="fixed inset-0 overflow-hidden pointer-events-none">
      <div
        class="absolute bottom-0 left-0 w-96 h-96 bg-[#fe6600]/10 rounded-full mix-blend-multiply filter blur-3xl"
      ></div>
      <div
        class="absolute top-0 right-0 w-96 h-96 bg-[#541049]/10 rounded-full mix-blend-multiply filter blur-3xl"
      ></div>
    </div>

    <!-- Navigation (Consistent) -->
    <LandingNav/>

    <main class="relative z-10">
      <!-- Policy Content Section -->
      <div class="pt-32 pb-24 px-6 sm:px-8 lg:px-10 policy-content">
        <div class="max-w-4xl mx-auto">
          <div class="text-center mb-12">
            <h1 class="text-4xl md:text-5xl font-bold">Privacy Policy</h1>
            <p class="text-lg text-gray-500 mt-4">
              Last Updated: October 27, 2023
            </p>
          </div>

          <article
            class="prose prose-lg lg:prose-xl max-w-none prose-headings:font-bold prose-a:text-[#fe6600] prose-a:no-underline hover:prose-a:underline"
          >
            <div
              class="bg-[#fff8f2] border-l-4 border-[#fe6600] p-6 rounded-r-lg mb-12 text-base"
            >
              <p class="font-semibold text-[#541049]">Important Notice:</p>
              <p class="mt-2 text-gray-700">
                This document is a template and for informational purposes only.
                It is not legal advice. You should consult with a qualified
                legal professional to ensure your privacy policy is compliant
                with all applicable laws and regulations for your specific
                business needs.
              </p>
            </div>

            <h2>1. Introduction</h2>
            <p>
              Welcome to Mollage Media. We are committed to protecting your
              privacy and handling your personal data in an open and transparent
              manner. This privacy policy ("Policy") explains how we collect,
              use, process, and disclose your information across the Mollage
              Media website and services (collectively, "Services").
            </p>

            <h2>2. Information We Collect</h2>
            <p>
              We collect information to provide and improve our services. The
              types of information we collect can be broken down into three
              categories:
            </p>
            <h3>a. Information You Provide to Us</h3>
            <p>
              This includes personal data you provide when you fill out a
              contact form, subscribe to our newsletter, or otherwise
              communicate with us. This information may include:
            </p>
            <ul>
              <li>Full Name</li>
              <li>Email Address</li>
              <li>Phone Number</li>
              <li>Company Name</li>
              <li>
                Any other information you choose to provide in your message.
              </li>
            </ul>

            <h3>b. Information We Collect Automatically</h3>
            <p>
              When you use our Services, we may automatically collect certain
              information about your device and usage. This information
              includes:
            </p>
            <ul>
              <li>
                <strong>Log and Usage Data:</strong> Service-related,
                diagnostic, usage, and performance information our servers
                automatically collect when you access or use our website.
              </li>
              <li>
                <strong>Cookies and Tracking Technologies:</strong> We use
                cookies and similar tracking technologies to track activity on
                our Services and hold certain information. You can instruct your
                browser to refuse all cookies or to indicate when a cookie is
                being sent.
              </li>
            </ul>

            <h2>3. How We Use Your Information</h2>
            <p>
              We use the information we collect for various business purposes,
              including to:
            </p>
            <ul>
              <li>Provide, operate, and maintain our Services.</li>
              <li>Respond to your inquiries, comments, and questions.</li>
              <li>
                Send you marketing and promotional communications, such as our
                newsletter (with your consent).
              </li>
              <li>Improve, personalize, and expand our Services.</li>
              <li>
                Understand and analyze how you use our Services to enhance user
                experience.
              </li>
              <li>Comply with legal obligations.</li>
            </ul>

            <h2>4. Information Sharing and Disclosure</h2>
            <p>
              We do not sell your personal data. We may share your information
              with third-party vendors, consultants, and other service providers
              who perform services on our behalf, such as website hosting, data
              analysis, and email delivery. We may also disclose your
              information if required to do so by law or in response to valid
              requests by public authorities.
            </p>

            <h2>5. Data Security</h2>
            <p>
              We use a combination of technical, administrative, and physical
              controls to maintain the security of your data. However, no method
              of transmission over the Internet or method of electronic storage
              is 100% secure. While we strive to use commercially acceptable
              means to protect your Personal Data, we cannot guarantee its
              absolute security.
            </p>

            <h2>6. Your Data Protection Rights</h2>
            <p>
              Depending on your location, you may have the following rights
              regarding your personal data:
            </p>
            <ul>
              <li>
                The right to access, update, or delete the information we have
                on you.
              </li>
              <li>The right of rectification.</li>
              <li>The right to object to processing.</li>
              <li>The right of restriction.</li>
              <li>The right to data portability.</li>
              <li>The right to withdraw consent at any time.</li>
            </ul>
            <p>
              To exercise any of these rights, please contact us using the
              details provided below.
            </p>

            <h2>7. Children's Privacy</h2>
            <p>
              Our Services are not intended for use by children under the age of
              13. We do not knowingly collect personally identifiable
              information from children under 13. If you become aware that a
              child has provided us with Personal Data, please contact us.
            </p>

            <h2>8. Changes to This Privacy Policy</h2>
            <p>
              We may update our Privacy Policy from time to time. We will notify
              you of any changes by posting the new Privacy Policy on this page
              and updating the "Last Updated" date at the top. You are advised
              to review this Privacy Policy periodically for any changes.
            </p>

            <h2>9. Contact Us</h2>
            <p>
              If you have any questions about this Privacy Policy, please
              contact us:
            </p>
            <ul>
              <li>
                By email:
                <a href="mailto:privacy@mollagemedia.com"
                  >privacy@mollagemedia.com</a
                >
              </li>
              <li>
                By mail: 123 Marketing Ave, Suite 400, San Francisco, CA 94107
              </li>
            </ul>
          </article>
        </div>
      </div>
    </main>

    <!-- Footer (Consistent) -->
<LandingFooter/>
  </div>
</template>

<script>
import { Icon } from "@iconify/vue";
import gsap from "gsap";

export default {
  name: "PrivacyPolicyPage",
  components: { Icon },
  data() {
    return {
      isMenuOpen: false,
    };
  },
  mounted() {
    gsap.from(".policy-content", {
      duration: 1.2,
      y: 30,
      opacity: 0,
      delay: 0.2,
      ease: "power3.out",
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
