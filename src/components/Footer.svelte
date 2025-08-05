<!-- src/components/Footer.svelte -->
<script>
  import {
    ArrowRight,
    Mail,
    Phone,
    MapPin,
    Twitter,
    Github,
    Linkedin,
  } from "lucide-svelte";

  export let year = new Date().getFullYear();
  export let name = "Your Brand";

  // Footer links data
  const quickLinks = [
    { text: "Home", href: "/" },
    { text: "Features", href: "#features" },
    { text: "Pricing", href: "/pricing" },
    { text: "Blog", href: "/blog" },
    { text: "Contact", href: "/contact" },
  ];

  const legalLinks = [
    { text: "Privacy Policy", href: "/privacy" },
    { text: "Terms of Service", href: "/terms" },
    { text: "Cookie Policy", href: "/cookies" },
  ];

  const contactInfo = [
    { icon: Mail, text: "hello@yourbrand.com" },
    { icon: Phone, text: "+1 (555) 123-4567" },
    { icon: MapPin, text: "123 Business Ave, City, Country" },
  ];

  const socialLinks = [
    { icon: Twitter, href: "https://twitter.com/yourbrand" },
    { icon: Github, href: "https://github.com/yourbrand" },
    { icon: Linkedin, href: "https://linkedin.com/company/yourbrand" },
  ];
</script>

<footer class="bg-gray-900 border-t border-gray-800 mt-20">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-10">
      <!-- Brand Column -->
      <div class="space-y-4">
        <h3 class="text-lg font-bold text-white">{name}</h3>
        <p class="text-gray-400">
          Building innovative solutions to help your business grow and succeed
          in the digital world.
        </p>
        <div class="flex space-x-4">
          {#each socialLinks as social}
            <a
              href={social.href}
              target="_blank"
              rel="noopener noreferrer"
              class="text-gray-400 hover:text-teal-400 transition-colors duration-200"
              aria-label={social.icon.name}
            >
              <social.icon class="h-5 w-5" />
            </a>
          {/each}
        </div>
      </div>

      <!-- Quick Links -->
      <div>
        <h3 class="text-lg font-bold text-white mb-4">Quick Links</h3>
        <ul class="space-y-2">
          {#each quickLinks as link}
            <li>
              <a
                href={link.href}
                class="text-gray-400 hover:text-teal-400 transition-colors duration-200 flex items-center"
              >
                <ArrowRight class="h-3 w-3 mr-2" />
                {link.text}
              </a>
            </li>
          {/each}
        </ul>
      </div>

      <!-- Legal -->
      <div>
        <h3 class="text-lg font-bold text-white mb-4">Legal</h3>
        <ul class="space-y-2">
          {#each legalLinks as link}
            <li>
              <a
                href={link.href}
                class="text-gray-400 hover:text-teal-400 transition-colors duration-200 flex items-center"
              >
                <ArrowRight class="h-3 w-3 mr-2" />
                {link.text}
              </a>
            </li>
          {/each}
        </ul>
      </div>

      <!-- Contact -->
      <div>
        <h3 class="text-lg font-bold text-white mb-4">Contact Us</h3>
        <ul class="space-y-3">
          {#each contactInfo as item}
            <li class="flex items-start">
              <item.icon
                class="h-5 w-5 text-teal-400 mt-0.5 mr-3 flex-shrink-0"
              />
              <span class="text-gray-400">{item.text}</span>
            </li>
          {/each}
        </ul>
      </div>
    </div>

    <!-- Newsletter -->
    <div class="mt-16 max-w-2xl mx-auto">
      <h3 class="text-lg font-bold text-white text-center mb-4">
        Subscribe to our newsletter
      </h3>
      <form class="flex flex-col sm:flex-row gap-3">
        <input
          type="email"
          placeholder="Your email address"
          class="flex-grow px-4 py-2 rounded-md bg-gray-800 border border-gray-700 text-white focus:outline-none focus:ring-2 focus:ring-teal-500"
          required
        />
        <button
          type="submit"
          class="px-6 py-2 bg-gradient-to-r from-teal-500 to-blue-600 hover:from-teal-600 hover:to-blue-700 text-white font-medium rounded-md transition-all duration-300"
        >
          Subscribe
        </button>
      </form>
      <p class="text-xs text-gray-500 mt-2 text-center">
        We'll never share your email. Unsubscribe at any time.
      </p>
    </div>

    <!-- Copyright -->
    <div
      class="mt-16 pt-8 border-t border-gray-800 flex flex-col md:flex-row justify-between items-center"
    >
      <p class="text-gray-400 text-sm">
        © {year}
        {name}. All rights reserved.
      </p>
      <div class="mt-4 md:mt-0 flex space-x-6">
        <a href="/" class="text-gray-400 hover:text-teal-400 text-sm"
          >Privacy Policy</a
        >
        <a href="/" class="text-gray-400 hover:text-teal-400 text-sm"
          >Terms of Service</a
        >
        <a href="/" class="text-gray-400 hover:text-teal-400 text-sm">Cookies</a
        >
      </div>
    </div>
  </div>
</footer>
