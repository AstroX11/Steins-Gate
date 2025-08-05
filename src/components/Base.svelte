<!-- src/components/Base.svelte -->
<script>
  import { onMount } from "svelte";
  import { fade, slide } from "svelte/transition";
  import { quintOut } from "svelte/easing";

  import {
    Rocket,
    Layout,
    Shield,
    Zap,
    ArrowRight,
    ChevronLeft,
    ChevronRight,
    Check,
    Users,
    Clock,
    Server,
  } from "lucide-svelte";

  export let title = "Let's build something cool";
  export let subtitle = "You're all set up and ready to go.";
  export let ctaText = "Get Started";
  export let ctaLink = "#";

  // Smooth scroll function
  const scrollTo = (id) => {
    const element = document.getElementById(id);
    if (element) {
      element.scrollIntoView({
        behavior: "smooth",
        block: "start",
      });
    }
  };

  // Header features with proper icons
  let features = [
    {
      icon: Rocket,
      title: "Lightning Fast",
      description: "Optimized for maximum performance",
    },
    {
      icon: Zap,
      title: "Efficient",
      description: "Minimal footprint, maximum output",
    },
    {
      icon: Shield,
      title: "Secure",
      description: "Built with security in mind",
    },
    {
      icon: Layout,
      title: "Responsive",
      description: "Works on all devices",
    },
  ];

  // Stats for the header
  let stats = [
    { value: "99.9%", label: "Uptime", icon: Server },
    { value: "10K+", label: "Users", icon: Users },
    { value: "24/7", label: "Support", icon: Clock },
  ];

  // Testimonials/slides
  let slides = [
    {
      id: 1,
      quote: "This platform transformed our business operations completely.",
      author: "Alex Johnson",
      role: "CEO, TechCorp",
      image: "./src/images/testimonial-1.jpg",
    },
    {
      id: 2,
      quote: "The easiest solution we've implemented with the fastest results.",
      author: "Maria Garcia",
      role: "Marketing Director",
      image: "./src/images/testimonial-2.jpg",
    },
    {
      id: 3,
      quote: "Our team productivity increased by 40% after switching.",
      author: "Sam Wilson",
      role: "Operations Manager",
      image: "./src/images/testimonial-3.jpg",
    },
  ];

  let currentSlide = 0;

  const nextSlide = () => {
    currentSlide = (currentSlide + 1) % slides.length;
  };

  const prevSlide = () => {
    currentSlide = (currentSlide - 1 + slides.length) % slides.length;
  };

  // Auto-advance slides
  onMount(() => {
    const interval = setInterval(nextSlide, 5000);
    return () => clearInterval(interval);
  });

  let fullscreenImage = null;

  function openFullscreen(src) {
    fullscreenImage = src;
    document.body.classList.add("overflow-hidden");
  }

  function closeFullscreen() {
    fullscreenImage = null;
    document.body.classList.remove("overflow-hidden");
  }
</script>

<main class="w-full max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
  <!-- Hero Section -->
  <div
    class="relative overflow-hidden bg-gradient-to-br from-gray-900 to-gray-800 rounded-2xl shadow-2xl mt-8"
  >
    <div
      class="absolute inset-0 bg-[url('data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAlIiBoZWlnaHQ9IjEwMCUiPjxkZWZzPjxwYXR0ZXJuIGlkPSJwYXR0ZXJuIiB3aWR0aD0iNDAiIGhlaWdodD0iNDAiIHBhdHRlcm5Vbml0cz0idXNlclNwYWNlT25Vc2UiIHBhdHRlcm5UcmFuc2Zvcm09InJvdGF0ZSg0NSkiPjxyZWN0IHdpZHRoPSIyMCIgaGVpZ2h0PSIyMCIgZmlsbD0icmdiYSgyNTUsMjU1LDI1NSwwLjAzKSIvPjwvcGF0dGVybj48L2RlZnM+PHJlY3Qgd2lkdGg9IjEwMCUiIGhlaWdodD0iMTAwJSIgZmlsbD0idXJsKCNwYXR0ZXJuKSIvPjwvc3ZnPg==')] opacity-20"
    ></div>

    <div class="relative px-4 py-16 sm:px-6 sm:py-24 lg:py-32 lg:px-8">
      <div class="text-center">
        <h1
          class="text-4xl font-extrabold tracking-tight text-white sm:text-5xl lg:text-6xl"
        >
          <span class="block">Welcome to My Landing Page</span>
          <span
            class="block text-transparent bg-clip-text bg-gradient-to-r from-teal-400 to-blue-500"
            >Next Generation Platform</span
          >
        </h1>

        <p class="mt-6 max-w-lg mx-auto text-xl text-gray-300">
          Built with <span class="text-teal-400 font-medium">Astro</span>,
          <span class="text-pink-400 font-medium">Svelte</span>, and
          <span class="text-blue-400 font-medium">Tailwind CSS</span>.
        </p>

        <div class="mt-10 flex justify-center gap-4">
          <a
            href={ctaLink}
            on:click|preventDefault={() => scrollTo("cta-section")}
            class="px-8 py-3 border border-transparent text-base font-medium rounded-md text-white bg-gradient-to-r from-teal-500 to-blue-600 hover:from-teal-600 hover:to-blue-700 shadow-lg hover:shadow-xl transition-all duration-300 flex items-center"
          >
            {ctaText}
            <ArrowRight class="ml-2 h-5 w-5" />
          </a>
          <a
            href="#features"
            on:click|preventDefault={() => scrollTo("features")}
            class="px-8 py-3 border border-transparent text-base font-medium rounded-md text-white bg-gray-700 hover:bg-gray-600 shadow hover:shadow-md transition-all duration-300"
          >
            Learn More
          </a>
        </div>
      </div>
    </div>
  </div>

  <!-- Stats Section -->
  <div class="bg-gray-800 rounded-xl shadow-lg -mt-12 relative z-10 mx-4">
    <div class="max-w-7xl mx-auto px-6 py-8">
      <div class="grid grid-cols-1 gap-8 sm:grid-cols-3">
        {#each stats as stat}
          <div class="text-center">
            <div class="flex justify-center">
              <stat.icon class="h-10 w-10 text-teal-400 mb-2" />
            </div>
            <p class="text-4xl font-extrabold text-white sm:text-5xl">
              {stat.value}
            </p>
            <p class="mt-2 text-lg font-medium text-gray-300">{stat.label}</p>
          </div>
        {/each}
      </div>
    </div>
  </div>

  <!-- Features Section -->
  <section id="features" class="py-16 sm:py-24" in:fade={{ duration: 500 }}>
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="lg:text-center">
        <h2
          class="text-base text-teal-400 font-semibold tracking-wide uppercase"
        >
          Features
        </h2>
        <p class="mt-2 text-3xl font-extrabold text-white sm:text-4xl">
          Everything you need to succeed
        </p>
      </div>

      <!-- Replace the features grid section with this corrected version -->
      <div class="mt-12">
        <div class="grid grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-4">
          {#each features as feature, index}
            <div
              class="pt-6"
              in:slide={{
                delay: 100 * index,
                duration: 500,
                easing: quintOut,
              }}
            >
              <div
                class="flow-root bg-gray-800 rounded-lg px-6 pb-8 h-full shadow-lg hover:shadow-xl transition-shadow duration-300"
              >
                <div class="-mt-6">
                  <div
                    class="flex items-center justify-center h-12 w-12 rounded-md bg-gradient-to-r from-teal-500 to-blue-500 text-white mx-auto"
                  >
                    <feature.icon class="h-6 w-6" />
                  </div>
                  <h3 class="mt-4 text-lg font-medium text-white text-center">
                    {feature.title}
                  </h3>
                  <p class="mt-2 text-base text-gray-300 text-center">
                    {feature.description}
                  </p>
                </div>
              </div>
            </div>
          {/each}
        </div>
      </div>
    </div>
  </section>

  <!-- Testimonial Slides -->
  <section class="py-16 bg-gray-800/50 rounded-xl my-12" in:fade>
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <h2 class="text-3xl font-extrabold text-white text-center mb-12">
        What Our Customers Say
      </h2>

      <div class="relative overflow-hidden">
        <div class="relative h-96">
          {#each slides as slide, index (slide.id)}
            {#if index === currentSlide}
              <div
                transition:fade={{ duration: 500 }}
                class="absolute inset-0 flex flex-col md:flex-row items-center justify-center gap-8 px-4"
              >
                <div class="w-full md:w-1/3 flex justify-center">
                  <div
                    class="h-48 w-48 rounded-full bg-gray-700 overflow-hidden shadow-lg"
                  >
                    <!-- Replace with your actual image -->
                    <img
                      src={slide.image}
                      alt={slide.author}
                      class="h-full w-full object-cover"
                    />
                  </div>
                </div>
                <div class="w-full md:w-2/3 text-center md:text-left">
                  <blockquote class="text-xl italic text-gray-300 mb-4">
                    "{slide.quote}"
                  </blockquote>
                  <div class="text-teal-400 font-medium">{slide.author}</div>
                  <div class="text-gray-400 text-sm">{slide.role}</div>
                </div>
              </div>
            {/if}
          {/each}
        </div>

        <button
          on:click={prevSlide}
          class="absolute left-4 top-1/2 -translate-y-1/2 bg-gray-800/80 hover:bg-gray-700 rounded-full p-2 shadow-md z-10"
          aria-label="Previous testimonial"
        >
          <ChevronLeft class="h-6 w-6 text-white" />
        </button>
        <button
          on:click={nextSlide}
          class="absolute right-4 top-1/2 -translate-y-1/2 bg-gray-800/80 hover:bg-gray-700 rounded-full p-2 shadow-md z-10"
          aria-label="Next testimonial"
        >
          <ChevronRight class="h-6 w-6 text-white" />
        </button>

        <div class="flex justify-center mt-6 gap-2">
          {#each slides as _, index (index)}
            <!-- svelte-ignore element_invalid_self_closing_tag -->
            <button
              on:click={() => (currentSlide = index)}
              class={`w-3 h-3 rounded-full ${index === currentSlide ? "bg-teal-400" : "bg-gray-500"}`}
              aria-label={`Go to slide ${index + 1}`}
            />
          {/each}
        </div>
      </div>
    </div>
  </section>

  <!-- Additional Content Section -->
  <section id="cta-section" class="py-16" in:fade>
    <div
      class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 bg-gray-800/50 rounded-xl p-8 shadow-lg"
    >
      <div class="text-center">
        <h2 class="text-3xl font-bold text-blue-400 mb-4">{title}</h2>
        <p class="text-xl text-gray-300 mb-8">{subtitle}</p>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-12">
          <div class="bg-gray-800 p-6 rounded-lg shadow-md">
            <h3 class="text-xl font-semibold text-white mb-3">Key Benefit 1</h3>
            <p class="text-gray-300">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do
              eiusmod tempor incididunt ut labore.
            </p>
          </div>
          <div class="bg-gray-800 p-6 rounded-lg shadow-md">
            <h3 class="text-xl font-semibold text-white mb-3">Key Benefit 2</h3>
            <p class="text-gray-300">
              Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
              nisi ut aliquip ex ea commodo.
            </p>
          </div>
        </div>

        <a
          href={ctaLink}
          class="inline-flex items-center px-8 py-3 border border-transparent text-base font-medium rounded-md text-white bg-gradient-to-r from-teal-500 to-blue-600 hover:from-teal-600 hover:to-blue-700 shadow-lg hover:shadow-xl transition-all duration-300"
        >
          {ctaText}
          <ArrowRight class="ml-2 h-5 w-5" />
        </a>
      </div>
    </div>
  </section>

  <!-- Gallery Section -->
  <section class="py-16" in:fade>
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <h2 class="text-3xl font-extrabold text-white text-center mb-12">
        Our Work
      </h2>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        {#each Array(6) as _, i}
          <div class="group relative">
            <div
              class="relative aspect-video bg-gray-700 overflow-hidden rounded-lg"
            >
              <!-- Image loads visibly by default -->
              <button
                type="button"
                class="block w-full h-full p-0 border-none bg-transparent cursor-zoom-in"
                on:click={() =>
                  openFullscreen(`./src/images/gallery-${i + 1}.jpg`)}
              >
                <img
                  src={`./src/images/gallery-${i + 1}.jpg`}
                  alt={`Project ${i + 1}`}
                  loading="lazy"
                  class="w-full h-full object-cover transition-transform duration-300 group-hover:scale-105 pointer-events-none"
                />
              </button>
            </div>
            <div
              class="absolute inset-0 bg-gradient-to-t from-black/30 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end p-4 pointer-events-none"
            >
              <h3 class="text-white text-lg font-medium">Project {i + 1}</h3>
            </div>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <!-- Add this modal at the bottom of your file -->
  {#if fullscreenImage}
    <div
      class="fixed inset-0 z-50 bg-black/90 flex items-center justify-center p-4"
      role="button"
      tabindex="0"
      aria-label="Close fullscreen image"
      on:click={closeFullscreen}
      on:keydown={(e) => {
        if (e.key === "Enter" || e.key === " ") {
          e.preventDefault();
          closeFullscreen();
        }
      }}
      transition:fade
    >
      <div class="relative max-w-6xl w-full">
        <button
          class="absolute -top-12 right-0 text-white hover:text-teal-400 transition-colors"
          on:click={closeFullscreen}
        >
          ✕ Close
        </button>
        <img
          src={fullscreenImage}
          class="max-w-full max-h-[90vh] object-contain mx-auto"
          alt="Fullscreen view"
        />
      </div>
    </div>
  {/if}

  <style>
    .cursor-zoom-in {
      cursor: zoom-in;
    }
    .overflow-hidden {
      overflow: hidden;
    }
  </style>
</main>
