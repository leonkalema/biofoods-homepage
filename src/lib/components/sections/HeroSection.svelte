<script lang="ts">
  import { onMount } from 'svelte';
  import { browser } from '$app/environment';
  
  let scrollY = 0;
  let parallaxOffset = 0;
  let textFloat = 0;
  let mouseX = 0;
  let mouseY = 0;
  let particles: Array<{x: number, y: number, id: number, delay: number}> = [];
  let particleId = 0;
  let time = 0;
  let isMenuOpen = false;
  let mounted = false;
  let heroRef: HTMLElement;
  
  onMount(() => {
    mounted = true;
    
    if (browser) {
      const updateScrollY = () => scrollY = window.scrollY;
      const updateMouse = (e: MouseEvent) => {
        mouseX = e.clientX / window.innerWidth;
        mouseY = e.clientY / window.innerHeight;
      };
      
      window.addEventListener('scroll', updateScrollY);
      window.addEventListener('mousemove', updateMouse);
      
      // Smooth animation loop
      const animate = () => {
        time += 0.02;
        requestAnimationFrame(animate);
      };
      animate();
      
      const interval = setInterval(() => {
        parallaxOffset += 0.01;
        textFloat += 0.02;
        time += 0.05;
      }, 16);

      // Generate floating particles
      for (let i = 0; i < 20; i++) {
        particles.push({
          x: Math.random() * 100,
          y: Math.random() * 100,
          id: particleId++,
          delay: Math.random() * 4
        });
      }

      return () => {
        window.removeEventListener('scroll', updateScrollY);
        window.removeEventListener('mousemove', updateMouse);
        clearInterval(interval);
      };
    }
  });
  
  // Liquid flow effects
  $: liquidFlow = scrollY * 0.5;
  $: waveOffset = Math.sin(time) * 30;
  $: mouseRipple = mouseX * 100;
  $: textMorph = Math.sin(time * 0.5) * 10;
</script>

<svelte:window bind:scrollY />

<section 
  bind:this={heroRef}
  class="relative min-h-screen overflow-hidden bg-gradient-to-br from-blue-900 via-purple-900 to-indigo-900"
>
  <!-- Integrated Navigation -->
  <nav class="absolute top-0 left-0 right-0 z-50 p-6 lg:p-8">
    <div class="flex items-center justify-between">
      <!-- BioFoods Logo -->
      <div class="flex items-center">
        <img 
          src="/bio-logo-no-strapline-2020.png" 
          alt="BioFoods Logo" 
          class="h-12 w-auto"
          style="transform: scale({1 + Math.sin(time * 1.5) * 0.02});"
        />
      </div>
      
      <!-- Liquid Navigation Menu -->
      <div class="hidden md:flex items-center space-x-8 text-white/90">
        <a href="/products" class="nav-link relative px-4 py-2 text-white/90 hover:text-white transition-all duration-300 hover:scale-105">
          Products
        </a>
        <a href="/about" class="nav-link relative px-4 py-2 text-white/90 hover:text-white transition-all duration-300 hover:scale-105">
          About
        </a>
        <a href="/sustainability" class="nav-link relative px-4 py-2 text-white/90 hover:text-white transition-all duration-300 hover:scale-105">
          Sustainability
        </a>
        <a href="/contact" class="nav-link relative px-4 py-2 text-white/90 hover:text-white transition-all duration-300 hover:scale-105">
          Contact
        </a>
      </div>
      
      <!-- Mobile Menu Button -->
      <button 
        class="md:hidden text-white p-2"
        on:click={() => isMenuOpen = !isMenuOpen}
        aria-label="Toggle menu"
      >
        <div class="w-6 h-0.5 bg-white mb-1 transition-all" class:rotate-45={isMenuOpen} class:translate-y-1.5={isMenuOpen}></div>
        <div class="w-6 h-0.5 bg-white mb-1 transition-all" class:opacity-0={isMenuOpen}></div>
        <div class="w-6 h-0.5 bg-white transition-all" class:-rotate-45={isMenuOpen} class:-translate-y-1.5={isMenuOpen}></div>
      </button>
    </div>
  </nav>
  
  <!-- Cinematic Video Background -->
  <video 
    autoplay 
    muted 
    loop 
    playsinline
    class="absolute inset-0 w-full h-full object-cover transition-transform duration-700 ease-out"
    style="
      transform: scale({1 + mouseY * 0.02}) translateX({mouseX * 0.5}px) translateY({mouseY * 0.3}px);
    "
  >
    <source src="https://cdn.midjourney.com/video/7fcbba12-c894-431d-8f60-c3dc45ef5978/2.mp4" type="video/mp4">
    <!-- Fallback image for browsers that don't support video or if video fails to load -->
    <img 
      src="https://cdn.midjourney.com/fd3a7a42-b653-458f-8290-84302474fe58/0_2.png" 
      alt="BioFoods Pastoral Landscape"
      class="absolute inset-0 w-full h-full object-cover"
    />
  </video>
  
  <!-- Atmospheric Overlay -->
  <div class="absolute inset-0 bg-gradient-to-b from-black/20 via-transparent to-black/40"></div>
  <!-- Subtle Color Overlay for Brand Consistency -->
  <div class="absolute inset-0 bg-gradient-to-br from-blue-900/20 via-transparent to-purple-900/20"></div>
  
  <!-- Floating Particles -->
  <div class="absolute inset-0 pointer-events-none">
    {#each particles as particle}
      <div 
        class="absolute w-2 h-2 bg-white/30 rounded-full blur-sm"
        style="
          left: {particle.x}%;
          top: {particle.y}%;
          animation-delay: {particle.delay}s;
          transform: translateY({Math.sin(time + particle.id * 0.5) * 30}px) translateX({Math.cos(time + particle.id * 0.3) * 20}px) scale({0.5 + Math.sin(time + particle.id) * 0.3});
        "
      ></div>
    {/each}
  </div>
  
  <!-- Mouse-following Atmospheric Effect -->
  <div 
    class="absolute w-96 h-96 bg-white/5 rounded-full blur-3xl transition-all duration-1000 ease-out pointer-events-none"
    style="
      left: {mouseX * 100}%;
      top: {mouseY * 100}%;
      transform: translate(-50%, -50%) scale({1 + Math.sin(time) * 0.2});
    "
  ></div>
  
  <!-- Hero Content -->
  <div class="relative z-20 flex items-center justify-center min-h-screen px-6 lg:px-12">
    <div class="max-w-6xl mx-auto text-center">
      <!-- Morphing Typography -->
      <div class="space-y-8">
        <h1 class="text-5xl md:text-7xl lg:text-8xl font-light leading-tight tracking-wide">
          <span 
            class="inline-block text-white drop-shadow-lg font-serif"
            style="
              transform: translateY({Math.sin(textFloat) * 5}px);
              text-shadow: 0 4px 20px rgba(0,0,0,0.3), 0 0 40px rgba(255,255,255,0.1);
            "
          >
            Pure
          </span>
          <br>
          <span 
            class="inline-block text-white/90 drop-shadow-lg font-serif italic"
            style="
              transform: translateY({Math.sin(textFloat + 1) * 3}px);
              text-shadow: 0 4px 20px rgba(0,0,0,0.3), 0 0 40px rgba(255,255,255,0.1);
            "
          >
            Goodness
          </span>
        </h1>
        
        <p 
          class="text-lg md:text-xl lg:text-2xl text-white/85 max-w-3xl mx-auto leading-relaxed font-light"
          style="
            transform: translateY({Math.sin(textFloat + 2) * 3}px);
            text-shadow: 0 2px 15px rgba(0,0,0,0.4);
          "
        >
          Where nature's finest ingredients meet artisanal craftsmanship, 
          creating pure, wholesome goodness for your family.
        </p>
      </div>
      
      <!-- Elegant Call-to-Action Links -->
      <div class="mt-16 flex flex-col sm:flex-row gap-12 justify-center items-center">
        <a 
          href="/about" 
          class="group relative text-white font-light text-lg tracking-wider uppercase transition-all duration-500 hover:scale-105 hover:text-green-200"
          style="transform: translateY({Math.sin(textFloat + 3) * 2}px);"
        >
          <span class="relative z-10 pb-2">Our Story</span>
          <div class="absolute bottom-0 left-0 w-0 h-px bg-gradient-to-r from-green-400 to-emerald-300 group-hover:w-full transition-all duration-500"></div>
        </a>
        
        <a 
          href="/products" 
          class="group relative text-white font-light text-lg tracking-wider uppercase transition-all duration-500 hover:scale-105 hover:text-red-200"
          style="transform: translateY({Math.sin(textFloat + 4) * 2}px);"
        >
          <span class="relative z-10 pb-2">Shop Now</span>
          <div class="absolute bottom-0 left-0 w-0 h-px bg-gradient-to-r from-red-400 to-rose-300 group-hover:w-full transition-all duration-500"></div>
        </a>
      </div>
    </div>
  </div>
  
  <!-- Animated Moving Scroll Indicator -->
  <div 
    class="absolute bottom-8 z-30 cursor-pointer group transition-all duration-1000 ease-in-out"
    style="left: {50 + Math.sin(time * 0.8) * 15}%; transform: translateX(-50%) translateY({Math.sin(time * 1.5) * 3}px);"
  >
    <div class="flex flex-col items-center space-y-2">
      <div class="w-px h-8 bg-gradient-to-b from-transparent via-white/60 to-transparent"></div>
      <div 
        class="w-2 h-2 rounded-full transition-all duration-500 group-hover:scale-125"
        style="background-color: {Math.sin(time * 0.8) > 0 ? 'rgb(74 222 128 / 0.8)' : 'rgb(248 113 113 / 0.8)'}; transform: translateY({Math.sin(time * 2) * 2}px);"
      ></div>
      <div class="w-px h-8 bg-gradient-to-b from-white/60 via-transparent to-transparent"></div>
    </div>
    <p 
      class="text-xs mt-3 text-center font-light tracking-wider uppercase transition-colors duration-500"
      style="color: {Math.sin(time * 0.8) > 0 ? 'rgb(134 239 172 / 0.6)' : 'rgb(252 165 165 / 0.6)'};"
    >
      {Math.sin(time * 0.8) > 0 ? 'Story' : 'Shop'}
    </p>
  </div>
</section>

<style>
  @keyframes float-slow {
    0%, 100% { transform: translateY(0px) rotate(0deg); }
    50% { transform: translateY(-20px) rotate(180deg); }
  }
  
  @keyframes float-medium {
    0%, 100% { transform: translateY(0px) rotate(0deg); }
    50% { transform: translateY(-15px) rotate(120deg); }
  }
  
  @keyframes float-fast {
    0%, 100% { transform: translateY(0px) rotate(0deg); }
    50% { transform: translateY(-25px) rotate(240deg); }
  }
  
  @keyframes pulse-slow {
    0%, 100% { opacity: 0.3; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(1.05); }
  }
  
  @keyframes pulse-slower {
    0%, 100% { opacity: 0.2; transform: scale(1); }
    50% { opacity: 0.4; transform: scale(1.1); }
  }
  
  @keyframes fade-in-up {
    from {
      opacity: 0;
      transform: translateY(30px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
</style>
