<script lang="ts">
  import { onMount } from 'svelte';
  import { browser } from '$app/environment';
  
  let sectionElement: HTMLElement;
  let isVisible = false;
  let mouseX = 0;
  let mouseY = 0;
  
  const achievements = [
    {
      icon: '🏆',
      title: 'Certified B-Corp',
      subtitle: 'Purpose-Driven Business',
      description: 'Leading the way in sustainable business practices across East Africa',
      color: 'from-emerald-400 to-green-500'
    },
    {
      icon: '🌍',
      title: 'East Africa Pioneer',
      subtitle: 'Innovation Leader',
      description: 'First to market with revolutionary dairy products and sustainable packaging',
      color: 'from-blue-400 to-cyan-500'
    },
    {
      icon: '🔬',
      title: 'R&D Excellence',
      subtitle: 'Continuous Innovation',
      description: 'State-of-the-art facilities driving next-generation food technology',
      color: 'from-purple-400 to-pink-500'
    },
    {
      icon: '🌱',
      title: 'Sustainability First',
      subtitle: '#GoSustainable',
      description: 'Carbon-neutral operations and regenerative farming partnerships',
      color: 'from-green-400 to-emerald-500'
    }
  ];
  
  onMount(() => {
    if (browser) {
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              isVisible = true;
            }
          });
        },
        { threshold: 0.2 }
      );
      
      if (sectionElement) {
        observer.observe(sectionElement);
      }
      
      const handleMouseMove = (e: MouseEvent) => {
        mouseX = (e.clientX / window.innerWidth - 0.5) * 20;
        mouseY = (e.clientY / window.innerHeight - 0.5) * 20;
      };
      
      window.addEventListener('mousemove', handleMouseMove);
      
      return () => {
        observer.disconnect();
        window.removeEventListener('mousemove', handleMouseMove);
      };
    }
  });
</script>

<section bind:this={sectionElement} class="relative min-h-screen bg-gradient-to-br from-gray-50 to-white overflow-hidden">
  
  <!-- Floating Background Elements -->
  <div class="absolute inset-0 pointer-events-none">
    <div 
      class="absolute top-20 left-10 w-64 h-64 bg-gradient-to-br from-emerald-400/20 to-green-500/20 rounded-full blur-3xl"
      style="transform: translateX({mouseX * 0.5}px) translateY({mouseY * 0.3}px);"
    ></div>
    <div 
      class="absolute bottom-20 right-10 w-80 h-80 bg-gradient-to-br from-blue-400/20 to-cyan-500/20 rounded-full blur-3xl"
      style="transform: translateX({mouseX * -0.3}px) translateY({mouseY * 0.4}px);"
    ></div>
  </div>
  
  <div class="relative z-10 max-w-7xl mx-auto px-6 lg:px-12 py-20">
    
    <!-- Section Header -->
    <div class="text-center mb-20">
      <div 
        class="transition-all duration-1000 ease-out {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}"
        style="transition-delay: 200ms;"
      >
        <h2 class="text-6xl lg:text-8xl font-extralight text-gray-900 mb-6">
          Innovation
          <span class="bg-gradient-to-r from-emerald-400 to-green-500 bg-clip-text text-transparent">
            Leadership
          </span>
        </h2>
        <p class="text-xl lg:text-2xl text-gray-600 font-light max-w-3xl mx-auto">
          Pioneering the future of sustainable food in East Africa through purpose-driven innovation
        </p>
      </div>
    </div>
    
    <!-- Achievement Cards -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
      {#each achievements as achievement, index}
        <div 
          class="group relative transition-all duration-1000 ease-out {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'}"
          style="transition-delay: {400 + index * 200}ms;"
        >
          
          <!-- Card Glow -->
          <div class="absolute -inset-4 bg-gradient-to-br {achievement.color} rounded-3xl opacity-0 group-hover:opacity-20 transition-all duration-700 filter blur-xl"></div>
          
          <!-- Main Card -->
          <div class="relative bg-white/80 backdrop-blur-md rounded-3xl p-8 shadow-xl border border-white/50 hover:shadow-2xl transition-all duration-700 hover:scale-105 hover:-translate-y-2">
            
            <!-- Icon -->
            <div class="text-5xl mb-6 text-center group-hover:scale-110 transition-transform duration-500">
              {achievement.icon}
            </div>
            
            <!-- Content -->
            <div class="text-center">
              <h3 class="text-2xl font-light text-gray-900 mb-2 group-hover:text-gray-700 transition-colors duration-300">
                {achievement.title}
              </h3>
              <p class="text-sm font-medium bg-gradient-to-r {achievement.color} bg-clip-text text-transparent mb-4">
                {achievement.subtitle}
              </p>
              <p class="text-gray-600 text-sm leading-relaxed">
                {achievement.description}
              </p>
            </div>
            
            <!-- Decorative Elements -->
            <div class="absolute top-4 right-4 w-8 h-8 bg-gradient-to-br {achievement.color} rounded-full opacity-10 group-hover:opacity-30 transition-all duration-500 group-hover:scale-125"></div>
          </div>
        </div>
      {/each}
    </div>
    
  </div>
</section>
