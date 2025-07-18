<script lang="ts">
  import { onMount } from 'svelte';
  
  interface Product {
    id: string;
    name: string;
    description: string;
    image: string;
    accent: string;
    category: string;
    tagline: string;
    story: string;
  }
  
  const products: Product[] = [
    {
      id: 'fresh-milk',
      name: 'Fresh Whole Milk',
      description: 'Pure, creamy whole milk from grass-fed cows.',
      image: 'https://biofoods.co.ke/wp-content/uploads/elementor/thumbs/fresh-whole_RT-2-q1gol0kf1tutgj2h0awikr4t7hr71s495v3t7nu6m8.jpg',
      accent: 'from-blue-400 via-cyan-300 to-teal-400',
      category: 'Essential',
      tagline: 'Pure Goodness',
      story: 'From pasture to table, our commitment to purity'
    },
    {
      id: 'yoghurt',
      name: 'Premium Yoghurt',
      description: 'Smooth, creamy yoghurt packed with live cultures.',
      image: 'https://biofoods.co.ke/wp-content/uploads/elementor/thumbs/orange-biscuits-450ml-Mockups-450ml-qbmhsy8mq5yky4h26olgewqiw2cg0lgj2xv4yr4jr4.png',
      accent: 'from-orange-400 via-amber-300 to-yellow-400',
      category: 'Probiotic',
      tagline: 'Living Culture',
      story: 'Billions of probiotics in every spoonful'
    },
    {
      id: 'whipping-cream',
      name: 'Whipping Cream',
      description: 'Rich, luxurious cream that whips to perfection.',
      image: 'https://biofoods.co.ke/wp-content/uploads/elementor/thumbs/whipping-cream_RT-q1gol0kf1tuk929jk2hwqk0b19gaz4q7zsmsatwge8.jpg',
      accent: 'from-purple-400 via-pink-300 to-rose-400',
      category: 'Premium',
      tagline: 'Culinary Magic',
      story: 'Transform ordinary moments into extraordinary'
    },
    {
      id: 'cheese',
      name: 'Artisanal Cheese',
      description: 'Handcrafted cheese with authentic flavor profiles.',
      image: 'https://biofoods.co.ke/wp-content/uploads/elementor/thumbs/85_RT-q1gol0kf1tuk929jk2hwqk0b19gaz4q7zsmsatwge8.jpg',
      accent: 'from-amber-400 via-orange-300 to-red-400',
      category: 'Gourmet',
      tagline: 'Artisan Craft',
      story: 'Aged to perfection, crafted with passion'
    },
    {
      id: 'butter',
      name: 'Bio Artisanal Butter',
      description: 'Creamy, salted butter made from the finest cream.',
      image: 'https://biofoods.co.ke/wp-content/uploads/elementor/thumbs/bio_butterBio-Artisanal-Butter-Salted_11_web-q1gol0kf1tuk929jk2hwqk0b19gaz4q7zsmsatwge8.png',
      accent: 'from-yellow-400 via-amber-300 to-orange-400',
      category: 'Artisanal',
      tagline: 'Golden Richness',
      story: 'Rich, creamy perfection in every spread'
    }
  ];
  
  let sectionElement: HTMLElement;
  let scrollY = 0;
  let innerHeight = 0;
  let isVisible = false;
  let hoveredProduct = -1;
  let mouseX = 0;
  let mouseY = 0;
  let animatedProducts: boolean[] = new Array(products.length).fill(false);
  
  onMount(() => {
    const handleScroll = () => {
      scrollY = window.scrollY;
    };
    
    const handleMouseMove = (e: MouseEvent) => {
      mouseX = e.clientX;
      mouseY = e.clientY;
    };
    
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            isVisible = true;
            // Stagger product animations
            products.forEach((_, index) => {
              setTimeout(() => {
                animatedProducts[index] = true;
                animatedProducts = [...animatedProducts];
              }, index * 300);
            });
          }
        });
      },
      { threshold: 0.1 }
    );
    
    window.addEventListener('scroll', handleScroll);
    window.addEventListener('mousemove', handleMouseMove);
    
    if (sectionElement) {
      observer.observe(sectionElement);
    }
    
    return () => {
      window.removeEventListener('scroll', handleScroll);
      window.removeEventListener('mousemove', handleMouseMove);
      observer.disconnect();
    };
  });
  
  $: parallaxOffset = scrollY * 0.3;
  $: mouseParallaxX = innerHeight ? (mouseX - innerWidth / 2) * 0.02 : 0;
  $: mouseParallaxY = innerHeight ? (mouseY - innerHeight / 2) * 0.02 : 0;
</script>

<svelte:window bind:innerHeight />

<section 
  bind:this={sectionElement}
  id="products" 
  class="relative min-h-screen bg-gradient-to-br from-slate-50 via-white to-green-50 overflow-hidden"
>
  <!-- Liquid Morphing Background -->
  <div class="absolute inset-0">
    <!-- Animated Liquid Blobs -->
    <div class="absolute inset-0">
      <div 
        class="absolute w-96 h-96 bg-gradient-to-br from-green-200/40 to-emerald-300/40 rounded-full filter blur-3xl animate-pulse"
        style="
          left: 10%;
          top: 20%;
          animation-duration: 8s;
          transform: translate({mouseParallaxX * 0.5}px, {mouseParallaxY * 0.3}px);
        "
      ></div>
      <div 
        class="absolute w-80 h-80 bg-gradient-to-br from-blue-200/40 to-cyan-300/40 rounded-full filter blur-3xl animate-pulse"
        style="
          right: 15%;
          top: 10%;
          animation-duration: 6s;
          animation-delay: 2s;
          transform: translate({mouseParallaxX * -0.3}px, {mouseParallaxY * 0.5}px);
        "
      ></div>
      <div 
        class="absolute w-72 h-72 bg-gradient-to-br from-purple-200/40 to-pink-300/40 rounded-full filter blur-3xl animate-pulse"
        style="
          left: 60%;
          bottom: 20%;
          animation-duration: 10s;
          animation-delay: 4s;
          transform: translate({mouseParallaxX * 0.4}px, {mouseParallaxY * -0.2}px);
        "
      ></div>
    </div>
  </div>
  
  <!-- Main Content -->
  <div class="relative z-10 max-w-7xl mx-auto px-6 py-20">
    
    <!-- Elegant Header -->
    <div class="text-center mb-20">
      <div 
        class="transition-all duration-1000 {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-20'}"
      >
        <div class="inline-block mb-6">
          <span class="text-sm font-light tracking-[0.3em] uppercase text-gray-500 bg-white/60 px-6 py-3 rounded-full backdrop-blur-sm border border-white/20">
            Our Collection
          </span>
        </div>
        <h2 class="text-6xl md:text-8xl font-extralight text-gray-900 mb-8 leading-none">
          Crafted with
          <span class="block bg-gradient-to-r from-green-600 via-emerald-500 to-teal-500 bg-clip-text text-transparent font-light">
            Passion
          </span>
        </h2>
        <p class="text-xl text-gray-600 max-w-2xl mx-auto font-light leading-relaxed">
          Each product tells a story of dedication, quality, and the pure essence of nature.
        </p>
      </div>
    </div>
    
    <!-- Floating Product Islands -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 lg:gap-12">
      {#each products as product, index}
        <div 
          class="group relative transition-all duration-1000 {animatedProducts[index] ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-20'}"
          style="transition-delay: {index * 200}ms;"
          on:mouseenter={() => hoveredProduct = index}
          on:mouseleave={() => hoveredProduct = -1}
        >
          <!-- Floating Product Island -->
          <div class="relative">
            <!-- Morphing Background Glow -->
            <div 
              class="absolute -inset-4 bg-gradient-to-br {product.accent} rounded-3xl opacity-0 group-hover:opacity-20 transition-all duration-700 filter blur-xl"
              style="transform: scale({hoveredProduct === index ? 1.1 : 1});"
            ></div>
            
            <!-- Main Product Card -->
            <div class="relative bg-white/80 backdrop-blur-sm rounded-3xl p-8 shadow-xl border border-white/20 hover:shadow-2xl transition-all duration-700 hover:scale-[1.02]">
              
              <!-- Category Badge -->
              <div class="absolute -top-3 left-8">
                <span class="text-xs font-medium tracking-wider uppercase text-white bg-gradient-to-r {product.accent} px-4 py-2 rounded-full shadow-lg">
                  {product.category}
                </span>
              </div>
              
              <!-- Product Image Container -->
              <div class="relative h-64 mb-6 overflow-hidden rounded-2xl">
                <div class="absolute inset-0 bg-gradient-to-br {product.accent} opacity-5"></div>
                <img 
                  src={product.image} 
                  alt={product.name}
                  class="w-full h-full object-contain p-4 transition-transform duration-700 group-hover:scale-110"
                  loading="lazy"
                />
                
                <!-- Floating Story Overlay -->
                <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-all duration-500 flex items-end p-6">
                  <p class="text-white text-sm font-light leading-relaxed">
                    {product.story}
                  </p>
                </div>
              </div>
              
              <!-- Product Info -->
              <div class="space-y-4">
                <div>
                  <h3 class="text-2xl font-light text-gray-900 mb-2 group-hover:text-gray-700 transition-colors duration-300">
                    {product.name}
                  </h3>
                  <p class="text-lg font-light bg-gradient-to-r {product.accent} bg-clip-text text-transparent">
                    {product.tagline}
                  </p>
                </div>
                
                <p class="text-gray-600 leading-relaxed font-light">
                  {product.description}
                </p>
                
                <!-- Interactive Button -->
                <div class="pt-4">
                  <button class="group/btn relative inline-flex items-center text-gray-900 font-light hover:text-white transition-all duration-500 overflow-hidden rounded-full px-6 py-3">
                    <span class="relative z-10 transition-colors duration-500">Explore</span>
                    <svg class="w-4 h-4 ml-2 transition-transform duration-300 group-hover/btn:translate-x-1 relative z-10" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
                    </svg>
                    <div class="absolute inset-0 bg-gradient-to-r {product.accent} scale-x-0 group-hover/btn:scale-x-100 transition-transform duration-500 origin-left rounded-full"></div>
                  </button>
                </div>
              </div>
              
              <!-- Subtle Accent Elements -->
              <div class="absolute top-4 right-4 w-12 h-12 bg-gradient-to-br {product.accent} rounded-full opacity-10 group-hover:opacity-20 transition-opacity duration-500"></div>
              <div class="absolute bottom-4 left-4 w-6 h-6 bg-gradient-to-br {product.accent} rounded-full opacity-20 group-hover:opacity-40 transition-all duration-500 group-hover:scale-125"></div>
            </div>
          </div>
        </div>
      {/each}
    </div>
    
    <!-- Bottom Call-to-Action -->
    <div 
      class="text-center mt-20 transition-all duration-1000 {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'}"
      style="transition-delay: 1200ms;"
    >
      <a 
        href="/products" 
        class="group inline-flex items-center text-lg font-light text-gray-700 hover:text-gray-900 transition-all duration-300"
      >
        <span class="relative">
          Discover Our Complete Collection
          <div class="absolute bottom-0 left-0 w-0 h-px bg-gradient-to-r from-green-500 to-emerald-400 group-hover:w-full transition-all duration-700"></div>
        </span>
        <svg class="w-5 h-5 ml-2 transition-transform duration-300 group-hover:translate-x-1" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
        </svg>
      </a>
    </div>
    
  </div>
</section>
