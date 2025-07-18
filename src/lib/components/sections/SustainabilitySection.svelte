<script lang="ts">
  import { onMount } from 'svelte';
  import { browser } from '$app/environment';
  
  let sectionElement: HTMLElement;
  let isVisible = false;
  let animatedMetrics = false;
  
  const metrics = [
    { value: '100%', label: 'Carbon Neutral Operations', icon: '🌍', color: 'from-green-400 to-emerald-500' },
    { value: '85%', label: 'Renewable Energy Usage', icon: '⚡', color: 'from-yellow-400 to-orange-500' },
    { value: '500+', label: 'Partner Farms', icon: '🚜', color: 'from-blue-400 to-cyan-500' },
    { value: '2M+', label: 'Plastic Bottles Saved', icon: '♻️', color: 'from-purple-400 to-pink-500' }
  ];
  
  const initiatives = [
    {
      title: 'Regenerative Farming',
      description: 'Working with local farmers to restore soil health and biodiversity',
      icon: '🌱',
      impact: 'Improved soil carbon by 40%'
    },
    {
      title: 'Circular Packaging',
      description: 'Innovative packaging solutions that eliminate single-use plastics',
      icon: '📦',
      impact: 'Zero waste to landfill'
    },
    {
      title: 'Community Wellness',
      description: 'Health and nutrition programs reaching 50,000+ families',
      icon: '❤️',
      impact: '50,000+ families reached'
    }
  ];
  
  onMount(() => {
    if (browser) {
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              isVisible = true;
              setTimeout(() => {
                animatedMetrics = true;
              }, 500);
            }
          });
        },
        { threshold: 0.2 }
      );
      
      if (sectionElement) {
        observer.observe(sectionElement);
      }
      
      return () => observer.disconnect();
    }
  });
</script>

<section bind:this={sectionElement} class="relative min-h-screen bg-gradient-to-br from-emerald-50 to-green-100 overflow-hidden">
  
  <!-- Organic Background Shapes -->
  <div class="absolute inset-0 pointer-events-none">
    <div class="absolute top-10 left-10 w-96 h-96 bg-gradient-to-br from-green-400/20 to-emerald-500/20 rounded-full blur-3xl animate-pulse"></div>
    <div class="absolute bottom-10 right-10 w-80 h-80 bg-gradient-to-br from-blue-400/20 to-cyan-500/20 rounded-full blur-3xl animate-pulse" style="animation-delay: 1s;"></div>
  </div>
  
  <div class="relative z-10 max-w-7xl mx-auto px-6 lg:px-12 py-20">
    
    <!-- Section Header -->
    <div class="text-center mb-20">
      <div 
        class="transition-all duration-1000 ease-out {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}"
        style="transition-delay: 200ms;"
      >
        <div class="inline-block bg-emerald-500/10 text-emerald-600 px-6 py-2 rounded-full text-sm font-medium mb-6">
          #GoSustainable
        </div>
        <h2 class="text-6xl lg:text-8xl font-extralight text-gray-900 mb-6">
          Sustainability
          <span class="bg-gradient-to-r from-emerald-400 to-green-500 bg-clip-text text-transparent">
            Impact
          </span>
        </h2>
        <p class="text-xl lg:text-2xl text-gray-600 font-light max-w-3xl mx-auto">
          Leading East Africa's transition to regenerative agriculture and circular economy
        </p>
      </div>
    </div>
    
    <!-- Impact Metrics -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 mb-20">
      {#each metrics as metric, index}
        <div 
          class="text-center transition-all duration-1000 ease-out {animatedMetrics ? 'opacity-100 translate-y-0 scale-100' : 'opacity-0 translate-y-8 scale-95'}"
          style="transition-delay: {600 + index * 200}ms;"
        >
          <div class="relative group">
            <!-- Metric Glow -->
            <div class="absolute -inset-4 bg-gradient-to-br {metric.color} rounded-3xl opacity-0 group-hover:opacity-20 transition-all duration-700 filter blur-xl"></div>
            
            <!-- Metric Card -->
            <div class="relative bg-white/80 backdrop-blur-md rounded-3xl p-8 shadow-xl border border-white/50 hover:shadow-2xl transition-all duration-700 hover:scale-105">
              <div class="text-4xl mb-4">{metric.icon}</div>
              <div class="text-4xl lg:text-5xl font-light bg-gradient-to-r {metric.color} bg-clip-text text-transparent mb-2">
                {metric.value}
              </div>
              <p class="text-gray-600 text-sm font-medium">{metric.label}</p>
            </div>
          </div>
        </div>
      {/each}
    </div>
    
    <!-- Sustainability Initiatives -->
    <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
      {#each initiatives as initiative, index}
        <div 
          class="group transition-all duration-1000 ease-out {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'}"
          style="transition-delay: {1000 + index * 300}ms;"
        >
          <div class="relative">
            <!-- Initiative Glow -->
            <div class="absolute -inset-4 bg-gradient-to-br from-emerald-400/20 to-green-500/20 rounded-3xl opacity-0 group-hover:opacity-40 transition-all duration-700 filter blur-xl"></div>
            
            <!-- Initiative Card -->
            <div class="relative bg-white/90 backdrop-blur-md rounded-3xl p-8 shadow-xl border border-white/60 hover:shadow-2xl transition-all duration-700 hover:scale-105 hover:-translate-y-2">
              <div class="text-5xl mb-6 group-hover:scale-110 transition-transform duration-500">
                {initiative.icon}
              </div>
              <h3 class="text-2xl font-light text-gray-900 mb-4">{initiative.title}</h3>
              <p class="text-gray-600 mb-6 leading-relaxed">{initiative.description}</p>
              <div class="inline-block bg-emerald-500/10 text-emerald-600 px-4 py-2 rounded-full text-sm font-medium">
                {initiative.impact}
              </div>
            </div>
          </div>
        </div>
      {/each}
    </div>
    
    <!-- Call to Action -->
    <div class="text-center mt-16">
      <div 
        class="transition-all duration-1000 ease-out {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}"
        style="transition-delay: 1800ms;"
      >
        <button class="bg-gradient-to-r from-emerald-500 to-green-600 text-white px-8 py-4 rounded-2xl font-medium hover:from-emerald-600 hover:to-green-700 transition-all duration-300 transform hover:scale-105 shadow-xl">
          Learn More About Our Impact
        </button>
      </div>
    </div>
    
  </div>
</section>
