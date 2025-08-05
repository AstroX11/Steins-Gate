<!-- src/components/Menu.svelte -->
<script>
  import { fade, fly } from "svelte/transition";
  import { quintOut } from "svelte/easing";

  let open = false;
</script>

<header class="w-full sticky top-0 z-50 bg-gray-950 border-b border-gray-800">
  <nav class="max-w-5xl mx-auto px-6 py-4 flex items-center justify-between">
    <div class="text-xl font-bold text-white">MySite</div>

    <!-- Hamburger for Mobile -->
    <button
      class="md:hidden focus:outline-none"
      on:click={() => (open = !open)}
      aria-label="Toggle menu"
    >
      <svg
        class="w-6 h-6 transition-transform duration-300"
        class:rotate-90={open}
        fill="none"
        stroke="currentColor"
        viewBox="0 0 24 24"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M4 6h16M4 12h16M4 18h16"
        ></path>
      </svg>
    </button>

    <!-- Desktop Menu -->
    <ul class="hidden md:flex gap-4 text-sm">
      <li>
        <a
          href="/"
          class="px-2 py-1 rounded-md hover:text-teal-400 hover:bg-gray-800 transition-all duration-200 ease-in-out"
          >Home</a
        >
      </li>
      <li>
        <a
          href="/about"
          class="px-2 py-1 rounded-md hover:text-teal-400 hover:bg-gray-800 transition-all duration-200 ease-in-out"
          >About</a
        >
      </li>
      <li>
        <a
          href="/services"
          class="px-2 py-1 rounded-md hover:text-teal-400 hover:bg-gray-800 transition-all duration-200 ease-in-out"
          >Services</a
        >
      </li>
      <li>
        <a
          href="/portfolio"
          class="px-2 py-1 rounded-md hover:text-teal-400 hover:bg-gray-800 transition-all duration-200 ease-in-out"
          >Portfolio</a
        >
      </li>
      <li>
        <a
          href="/blog"
          class="px-2 py-1 rounded-md hover:text-teal-400 hover:bg-gray-800 transition-all duration-200 ease-in-out"
          >Blog</a
        >
      </li>
      <li>
        <a
          href="/contact"
          class="px-2 py-1 rounded-md hover:text-teal-400 hover:bg-gray-800 transition-all duration-200 ease-in-out"
          >Contact</a
        >
      </li>
    </ul>
  </nav>

  <!-- Mobile Dropdown -->
  {#if open}
    <div
      in:fly={{ y: -20, duration: 300, easing: quintOut }}
      out:fly={{ y: -20, duration: 200, easing: quintOut }}
      class="md:hidden bg-gradient-to-b from-gray-900 to-gray-950 border-t border-gray-700 shadow-2xl"
    >
      <ul class="px-4 py-2 flex flex-col gap-1 text-sm" in:fade out:fade>
        <li>
          <a
            href="/"
            class="block py-2 px-3 rounded-lg hover:bg-gray-800 hover:text-teal-400 transition-all duration-200 ease-in-out border-l-4 border-transparent hover:border-teal-400"
          >
            Home
          </a>
        </li>
        <li>
          <a
            href="/about"
            class="block py-2 px-3 rounded-lg hover:bg-gray-800 hover:text-teal-400 transition-all duration-200 ease-in-out border-l-4 border-transparent hover:border-teal-400"
          >
            About
          </a>
        </li>
        <li>
          <a
            href="/services"
            class="block py-2 px-3 rounded-lg hover:bg-gray-800 hover:text-teal-400 transition-all duration-200 ease-in-out border-l-4 border-transparent hover:border-teal-400"
          >
            Services
          </a>
        </li>
        <li>
          <a
            href="/portfolio"
            class="block py-2 px-3 rounded-lg hover:bg-gray-800 hover:text-teal-400 transition-all duration-200 ease-in-out border-l-4 border-transparent hover:border-teal-400"
          >
            Portfolio
          </a>
        </li>
        <li>
          <a
            href="/blog"
            class="block py-2 px-3 rounded-lg hover:bg-gray-800 hover:text-teal-400 transition-all duration-200 ease-in-out border-l-4 border-transparent hover:border-teal-400"
          >
            Blog
          </a>
        </li>
        <li>
          <a
            href="/contact"
            class="block py-2 px-3 rounded-lg hover:bg-gray-800 hover:text-teal-400 transition-all duration-200 ease-in-out border-l-4 border-transparent hover:border-teal-400"
          >
            Contact
          </a>
        </li>
      </ul>
    </div>
  {/if}
</header>
