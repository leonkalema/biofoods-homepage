<script lang="ts">
  import { onMount } from 'svelte';
  
  interface JourneyStep {
    id: string;
    number: number;
    title: string;
    subtitle: string;
    description: string;
    icon: string;
    character: string;
    color: string;
    bgGradient: string;
  }
  
  const journeySteps: JourneyStep[] = [
    {
      id: 'farm',
      number: 1,
      title: 'Farm',
      subtitle: 'Where it all begins',
      description: 'Happy cows grazing on lush, organic pastures under the open sky. Every drop of milk starts with love and care.',
      icon: 'M12 2L2 7v10c0 5.55 3.84 10 9 11 1.16-.21 2.31-.48 3.38-.84',
      character: '🐄',
      color: 'from-green-400 to-emerald-500',
      bgGradient: 'from-green-100 to-emerald-50'
    },
    {
      id: 'collection',
      number: 2,
      title: 'Collection',
      subtitle: 'Gentle gathering',
      description: 'Fresh milk collected with care, maintaining the perfect temperature and purity from the very first moment.',
      icon: 'M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16',
      character: '🥛',
      color: 'from-blue-400 to-cyan-500',
      bgGradient: 'from-blue-100 to-cyan-50'
    },
    {
      id: 'processing',
      number: 3,
      title: 'Processing',
      subtitle: 'Artisan craftsmanship',
      description: 'Minimal processing with maximum care. We preserve every nutrient while creating products that delight your senses.',
      icon: 'M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z',
      character: '⚙️',
      color: 'from-purple-400 to-pink-500',
      bgGradient: 'from-purple-100 to-pink-50'
    },
    {
      id: 'store',
      number: 4,
      title: 'In Store',
      subtitle: 'Ready for you',
      description: 'Our products arrive fresh at your local store, perfectly preserved and ready to bring joy to your table.',
      icon: 'M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z',
      character: '🏪',
      color: 'from-orange-400 to-red-500',
      bgGradient: 'from-orange-100 to-red-50'
    },
    {
      id: 'you',
      number: 5,
      title: 'You!',
      subtitle: 'The final destination',
      description: 'From grass to glass, every step leads to this moment - pure, delicious nutrition for you and your family.',
      icon: 'M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z',
      character: '👨‍👩‍👧‍👦',
      color: 'from-emerald-400 to-green-500',
      bgGradient: 'from-emerald-100 to-green-50'
    }
  ];
  
  let sectionElement: HTMLElement;
  let scrollY = 0;
  let innerHeight = 0;
  let isVisible = false;
  let activeStep = 0;
  let mouseX = 0;
  let mouseY = 0;
  let stepElements: HTMLElement[] = [];
  let animatedSteps: boolean[] = new Array(journeySteps.length).fill(false);
  
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
            // Animate steps in sequence with much slower, more dramatic timing
            journeySteps.forEach((_, index) => {
              setTimeout(() => {
                animatedSteps[index] = true;
                animatedSteps = [...animatedSteps];
              }, index * 1800); // Increased from 800ms to 1800ms for slower reveal
            });
          }
        });
      },
      { threshold: 0.1 } // Lower threshold for earlier trigger
    );
    
    // Track active step based on scroll position
    const updateActiveStep = () => {
      if (stepElements.length === 0) return;
      
      const sectionTop = sectionElement?.offsetTop || 0;
      const scrollPosition = scrollY + innerHeight / 2;
      
      stepElements.forEach((element, index) => {
        const elementTop = element.offsetTop + sectionTop;
        const elementBottom = elementTop + element.offsetHeight;
        
        if (scrollPosition >= elementTop && scrollPosition <= elementBottom) {
          activeStep = index;
        }
      });
    };
    
    window.addEventListener('scroll', handleScroll);
    window.addEventListener('scroll', updateActiveStep);
    window.addEventListener('mousemove', handleMouseMove);
    
    if (sectionElement) {
      observer.observe(sectionElement);
    }
    
    return () => {
      window.removeEventListener('scroll', handleScroll);
      window.removeEventListener('scroll', updateActiveStep);
      window.removeEventListener('mousemove', handleMouseMove);
      observer.disconnect();
    };
  });
  
  $: parallaxOffset = scrollY * 0.1;
  $: mouseParallaxX = innerHeight ? (mouseX - window.innerWidth / 2) * 0.01 : 0;
  $: mouseParallaxY = innerHeight ? (mouseY - innerHeight / 2) * 0.01 : 0;
</script>

<svelte:window bind:innerHeight />

<section 
  bind:this={sectionElement}
  id="bio-way" 
  class="relative min-h-screen bg-gradient-to-br from-slate-50 via-white to-green-50 overflow-hidden"
>
  <!-- Floating Background Elements -->
  <div class="absolute inset-0">
    <!-- Animated Organic Shapes -->
    <div class="absolute inset-0">
      <div 
        class="absolute w-64 h-64 bg-gradient-to-br from-green-200/30 to-emerald-300/30 rounded-full filter blur-3xl animate-pulse"
        style="
          left: 5%;
          top: 15%;
          animation-duration: 12s;
          transform: translate({mouseParallaxX * 0.3}px, {mouseParallaxY * 0.2}px);
        "
      ></div>
      <div 
        class="absolute w-48 h-48 bg-gradient-to-br from-blue-200/30 to-cyan-300/30 rounded-full filter blur-3xl animate-pulse"
        style="
          right: 10%;
          top: 25%;
          animation-duration: 8s;
          animation-delay: 3s;
          transform: translate({mouseParallaxX * -0.2}px, {mouseParallaxY * 0.4}px);
        "
      ></div>
      <div 
        class="absolute w-56 h-56 bg-gradient-to-br from-purple-200/30 to-pink-300/30 rounded-full filter blur-3xl animate-pulse"
        style="
          left: 70%;
          bottom: 30%;
          animation-duration: 15s;
          animation-delay: 6s;
          transform: translate({mouseParallaxX * 0.4}px, {mouseParallaxY * -0.3}px);
        "
      ></div>
    </div>
  </div>
  
  <!-- Main Content -->
  <div class="relative z-10 max-w-7xl mx-auto px-6 py-20">
    
    <!-- Epic Header -->
    <div class="text-center mb-24">
      <div 
        class="transition-all duration-1000 {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-20'}"
      >
        <div class="inline-block mb-8">
          <span class="text-sm font-light tracking-[0.4em] uppercase text-gray-500 bg-white/60 px-8 py-4 rounded-full backdrop-blur-sm border border-white/20">
            Our Journey
          </span>
        </div>
        <h2 class="text-7xl md:text-9xl font-extralight text-gray-900 mb-8 leading-none">
          Quality from
          <span class="block bg-gradient-to-r from-green-600 via-emerald-500 to-teal-500 bg-clip-text text-transparent font-light">
            Grass to Glass
          </span>
        </h2>
        <p class="text-2xl text-gray-600 max-w-3xl mx-auto font-light leading-relaxed">
          Follow the extraordinary journey of our products through five magical steps
        </p>
      </div>
    </div>
    
    <!-- Interactive Journey Path -->
    <div class="relative">
      
      <!-- Animated Journey Line -->
      <div class="absolute left-1/2 top-0 bottom-0 w-1 transform -translate-x-1/2">
        <div class="h-full bg-gradient-to-b from-green-400 via-blue-400 via-purple-400 via-orange-400 to-emerald-400 rounded-full opacity-30"></div>
        
        <!-- Flowing Animation -->
        <div 
          class="absolute top-0 w-2 h-32 bg-gradient-to-b from-green-400 to-transparent rounded-full animate-pulse"
          style="
            left: 50%;
            transform: translateX(-50%) translateY({scrollY * 0.5}px);
            animation-duration: 3s;
          "
        ></div>
      </div>
      
      <!-- Horizontal Journey Timeline -->
      <div class="relative">
        
        <!-- Horizontal Journey Line -->
        <div class="absolute top-1/2 left-0 right-0 h-1 transform -translate-y-1/2">
          <div class="h-full bg-gradient-to-r from-green-400 via-blue-400 via-purple-400 via-orange-400 to-emerald-400 rounded-full opacity-30"></div>
          
          <!-- Flowing Animation -->
          <div 
            class="absolute top-1/2 left-0 w-32 h-2 bg-gradient-to-r from-green-400 to-transparent rounded-full animate-pulse transform -translate-y-1/2"
            style="
              transform: translateY(-50%) translateX({scrollY * 0.3}px);
              animation-duration: 3s;
            "
          ></div>
        </div>
        
        <!-- Journey Steps Grid -->
        <div class="grid grid-cols-1 md:grid-cols-3 lg:grid-cols-5 gap-8 lg:gap-6">
          {#each journeySteps as step, index}
            <div 
              bind:this={stepElements[index]}
              class="relative group"
            >
              
              <!-- Step Content -->
              <div 
                class="transition-all duration-[2000ms] ease-out {animatedSteps[index] ? 'opacity-100 translate-x-0 translate-y-0 scale-100 rotate-0' : 'opacity-0 translate-y-16 scale-95 -rotate-1'}"
                style="transition-delay: {index * 400}ms;"
              >
                <!-- Compact Floating Step Card -->
                <div class="relative">
                  
                  <!-- Epic Morphing Glow with Multiple Layers -->
                  <div 
                    class="absolute -inset-4 bg-gradient-to-br {step.color} rounded-2xl opacity-0 group-hover:opacity-30 transition-all duration-[1500ms] filter blur-xl"
                    style="transform: scale({activeStep === index ? 1.2 : 1}) rotate({activeStep === index ? 2 : 0}deg);"
                  ></div>
                  <div 
                    class="absolute -inset-2 bg-gradient-to-br {step.color} rounded-xl opacity-0 group-hover:opacity-15 transition-all duration-[1200ms] filter blur-lg"
                    style="transform: scale({activeStep === index ? 1.1 : 1}) rotate({activeStep === index ? -1 : 0}deg);"
                  ></div>
                  
                  <!-- Floating Particles -->
                  <div class="absolute inset-0 pointer-events-none">
                    <div 
                      class="absolute w-1.5 h-1.5 bg-gradient-to-br {step.color} rounded-full opacity-0 group-hover:opacity-60 transition-all duration-[2000ms] animate-bounce"
                      style="
                        top: 10%;
                        right: -8px;
                        animation-delay: {index * 300}ms;
                        animation-duration: 3s;
                      "
                    ></div>
                    <div 
                      class="absolute w-1 h-1 bg-gradient-to-br {step.color} rounded-full opacity-0 group-hover:opacity-40 transition-all duration-[2500ms] animate-pulse"
                      style="
                        bottom: 20%;
                        left: -6px;
                        animation-delay: {index * 500}ms;
                        animation-duration: 4s;
                      "
                    ></div>
                    <div 
                      class="absolute w-0.5 h-0.5 bg-gradient-to-br {step.color} rounded-full opacity-0 group-hover:opacity-50 transition-all duration-[1800ms] animate-ping"
                      style="
                        top: 70%;
                        right: -4px;
                        animation-delay: {index * 700}ms;
                        animation-duration: 2s;
                      "
                    ></div>
                  </div>
                  
                  <!-- Compact Main Card with Enhanced Effects -->
                  <div class="relative bg-white/95 backdrop-blur-md rounded-2xl p-6 shadow-[0_15px_35px_-8px_rgba(0,0,0,0.2)] border border-white/40 hover:shadow-[0_25px_45px_-8px_rgba(0,0,0,0.25)] transition-all duration-[1500ms] hover:scale-[1.05] hover:-translate-y-2 hover:rotate-1 group-hover:bg-white/98">
                    
                    <!-- Compact Animated Step Number Badge -->
                    <div class="absolute -top-4 left-1/2 transform -translate-x-1/2">
                      <div 
                        class="w-12 h-12 bg-gradient-to-br {step.color} rounded-full flex items-center justify-center shadow-xl transition-all duration-[1000ms] group-hover:scale-110 group-hover:rotate-12 group-hover:shadow-2xl"
                        style="box-shadow: 0 8px 20px -4px rgba(0,0,0,0.25), 0 0 15px rgba(34, 197, 94, 0.3);"
                      >
                        <span class="text-lg font-bold text-white transition-transform duration-500 group-hover:scale-110">{step.number}</span>
                      </div>
                      
                      <!-- Orbiting Ring -->
                      <div 
                        class="absolute inset-0 w-12 h-12 border border-gradient-to-br {step.color} rounded-full opacity-0 group-hover:opacity-30 transition-all duration-[2000ms]"
                        style="animation: spin 8s linear infinite;"
                      ></div>
                    </div>
                    
                    <!-- Compact Enhanced Character Icon with Animation -->
                    <div 
                      class="text-4xl mb-4 text-center transition-all duration-[1200ms] group-hover:scale-110 group-hover:rotate-6 filter drop-shadow-lg"
                      style="transition-delay: {index * 100}ms;"
                    >
                      {step.character}
                    </div>
                    
                    <!-- Compact Enhanced Content with Staggered Animations -->
                    <div class="text-center">
                      <h3 
                        class="text-xl font-light text-gray-900 mb-2 group-hover:text-gray-700 transition-all duration-[800ms] group-hover:scale-105"
                        style="transition-delay: {index * 150}ms;"
                      >
                        {step.title}
                      </h3>
                      <p 
                        class="text-sm font-light bg-gradient-to-r {step.color} bg-clip-text text-transparent mb-3 transition-all duration-[1000ms] group-hover:scale-105"
                        style="transition-delay: {index * 200}ms;"
                      >
                        {step.subtitle}
                      </p>
                      <p 
                        class="text-gray-600 leading-relaxed font-light text-xs transition-all duration-[1200ms] group-hover:text-gray-700"
                        style="transition-delay: {index * 250}ms;"
                      >
                        {step.description}
                      </p>
                    </div>
                    
                    <!-- Compact Enhanced Decorative Elements -->
                    <div class="absolute top-2 right-2 w-8 h-8 bg-gradient-to-br {step.color} rounded-full opacity-5 group-hover:opacity-15 transition-all duration-[1500ms] group-hover:scale-125 group-hover:rotate-45"></div>
                    <div class="absolute bottom-2 left-2 w-4 h-4 bg-gradient-to-br {step.color} rounded-full opacity-10 group-hover:opacity-30 transition-all duration-[1200ms] group-hover:scale-150 group-hover:-rotate-45"></div>
                    
                    <!-- Subtle Border Glow -->
                    <div class="absolute inset-0 rounded-2xl bg-gradient-to-br {step.color} opacity-0 group-hover:opacity-10 transition-all duration-[1500ms] pointer-events-none"></div>
                  </div>
                </div>
              </div>
              
              <!-- Enhanced Central Journey Node -->
              <div class="absolute left-1/2 -bottom-6 transform -translate-x-1/2 z-20">
                <div 
                  class="w-6 h-6 bg-gradient-to-br {step.color} rounded-full shadow-xl transition-all duration-[1000ms] {activeStep === index ? 'scale-150 shadow-2xl' : 'scale-100'}"
                  style="box-shadow: 0 0 25px rgba(34, 197, 94, 0.5), 0 0 50px rgba(34, 197, 94, 0.2);"
                ></div>
                
                <!-- Enhanced Pulsing Rings -->
                {#if activeStep === index}
                  <div class="absolute inset-0 w-6 h-6 bg-gradient-to-br {step.color} rounded-full animate-ping opacity-40" style="animation-duration: 2s;"></div>
                  <div class="absolute -inset-1 w-8 h-8 bg-gradient-to-br {step.color} rounded-full animate-pulse opacity-20" style="animation-duration: 3s;"></div>
                  <div class="absolute -inset-2 w-10 h-10 bg-gradient-to-br {step.color} rounded-full animate-ping opacity-10" style="animation-duration: 4s;"></div>
                {/if}
                
                <!-- Orbiting Particles -->
                <div 
                  class="absolute inset-0 w-6 h-6 transition-all duration-[1500ms] {activeStep === index ? 'opacity-100' : 'opacity-0'}"
                  style="animation: spin 6s linear infinite;"
                >
                  <div class="absolute -top-0.5 left-1/2 w-1 h-1 bg-gradient-to-br {step.color} rounded-full transform -translate-x-1/2"></div>
                  <div class="absolute top-1/2 -right-0.5 w-0.5 h-0.5 bg-gradient-to-br {step.color} rounded-full transform -translate-y-1/2"></div>
                  <div class="absolute -bottom-0.5 left-1/2 w-0.5 h-0.5 bg-gradient-to-br {step.color} rounded-full transform -translate-x-1/2"></div>
                </div>
              </div>
              
            </div>
          {/each}
        </div>
      </div>
    </div>
    
    <!-- Bottom Call-to-Action -->
    <div 
      class="text-center mt-32 transition-all duration-1000 {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'}"
      style="transition-delay: 2000ms;"
    >
      <div class="inline-block bg-white/80 backdrop-blur-sm rounded-3xl p-12 shadow-xl border border-white/20">
        <h3 class="text-3xl font-light text-gray-900 mb-6">
          Experience the <span class="bg-gradient-to-r from-green-600 to-emerald-500 bg-clip-text text-transparent">Bio Difference</span>
        </h3>
        <p class="text-gray-600 mb-8 text-lg font-light leading-relaxed max-w-2xl">
          Every product carries the story of this journey - from the first blade of grass to the moment it reaches your family.
        </p>
        <a 
          href="/about" 
          class="group inline-flex items-center text-lg font-light text-gray-700 hover:text-white transition-all duration-500 overflow-hidden rounded-full px-8 py-4"
        >
          <span class="relative z-10 transition-colors duration-500">Learn Our Story</span>
          <svg class="w-5 h-5 ml-2 transition-transform duration-300 group-hover:translate-x-1 relative z-10" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
          </svg>
          <div class="absolute inset-0 bg-gradient-to-r from-green-500 to-emerald-400 scale-x-0 group-hover:scale-x-100 transition-transform duration-500 origin-left rounded-full"></div>
        </a>
      </div>
    </div>
    
  </div>
</section>
