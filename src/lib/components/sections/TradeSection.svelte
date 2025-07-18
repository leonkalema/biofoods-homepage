<script lang="ts">
  import { onMount } from 'svelte';
  import { browser } from '$app/environment';
  
  let sectionElement: HTMLElement;
  let isVisible = false;
  let activeTab = 'distributor';
  
  const territories = [
    { name: 'East Africa', markets: 'Kenya, Uganda, Tanzania', status: 'Active' },
    { name: 'West Africa', markets: 'Ghana, Nigeria, Senegal', status: 'Expanding' },
    { name: 'Southern Africa', markets: 'South Africa, Botswana', status: 'Available' }
  ];
  
  const resources = [
    { name: 'Product Specifications', type: 'PDF', size: '2.4MB', icon: '📋' },
    { name: 'Certification Documents', type: 'ZIP', size: '5.1MB', icon: '🏆' },
    { name: 'Marketing Materials', type: 'ZIP', size: '12.3MB', icon: '📸' },
    { name: 'Pricing & Terms', type: 'PDF', size: '1.8MB', icon: '💰' }
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
      
      return () => observer.disconnect();
    }
  });
</script>

<section bind:this={sectionElement} class="relative min-h-screen bg-gradient-to-br from-slate-900 to-gray-900 text-white overflow-hidden">
  
  <!-- Background Pattern -->
  <div class="absolute inset-0 opacity-10">
    <div class="absolute inset-0" style="background-image: radial-gradient(circle at 25% 25%, #10b981 0%, transparent 50%), radial-gradient(circle at 75% 75%, #3b82f6 0%, transparent 50%);"></div>
  </div>
  
  <div class="relative z-10 max-w-7xl mx-auto px-6 lg:px-12 py-20">
    
    <!-- Section Header -->
    <div class="text-center mb-16">
      <div 
        class="transition-all duration-1000 ease-out {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}"
        style="transition-delay: 200ms;"
      >
        <h2 class="text-6xl lg:text-8xl font-extralight mb-6">
          Trade
          <span class="bg-gradient-to-r from-emerald-400 to-blue-400 bg-clip-text text-transparent">
            Partners
          </span>
        </h2>
        <p class="text-xl lg:text-2xl text-gray-300 font-light max-w-3xl mx-auto">
          Join our global network of distributors and retailers bringing premium dairy to markets worldwide
        </p>
      </div>
    </div>
    
    <!-- Tab Navigation -->
    <div class="flex justify-center mb-12">
      <div class="bg-white/10 backdrop-blur-md rounded-2xl p-2 border border-white/20">
        <button 
          class="px-6 py-3 rounded-xl transition-all duration-300 {activeTab === 'distributor' ? 'bg-emerald-500 text-white' : 'text-gray-300 hover:text-white'}"
          on:click={() => activeTab = 'distributor'}
        >
          Become a Distributor
        </button>
        <button 
          class="px-6 py-3 rounded-xl transition-all duration-300 {activeTab === 'resources' ? 'bg-emerald-500 text-white' : 'text-gray-300 hover:text-white'}"
          on:click={() => activeTab = 'resources'}
        >
          Trade Resources
        </button>
        <button 
          class="px-6 py-3 rounded-xl transition-all duration-300 {activeTab === 'territories' ? 'bg-emerald-500 text-white' : 'text-gray-300 hover:text-white'}"
          on:click={() => activeTab = 'territories'}
        >
          Available Territories
        </button>
      </div>
    </div>
    
    <!-- Tab Content -->
    <div class="max-w-4xl mx-auto">
      
      {#if activeTab === 'distributor'}
        <!-- Distributor Form -->
        <div class="bg-white/10 backdrop-blur-md rounded-3xl p-8 border border-white/20">
          <h3 class="text-3xl font-light mb-6 text-center">Distributor Interest Form</h3>
          <form class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <input type="text" placeholder="Company Name" class="bg-white/10 border border-white/20 rounded-xl px-4 py-3 text-white placeholder-gray-400">
            <input type="email" placeholder="Email Address" class="bg-white/10 border border-white/20 rounded-xl px-4 py-3 text-white placeholder-gray-400">
            <input type="tel" placeholder="Phone Number" class="bg-white/10 border border-white/20 rounded-xl px-4 py-3 text-white placeholder-gray-400">
            <select class="bg-white/10 border border-white/20 rounded-xl px-4 py-3 text-white">
              <option value="">Select Territory</option>
              <option value="east-africa">East Africa</option>
              <option value="west-africa">West Africa</option>
              <option value="southern-africa">Southern Africa</option>
              <option value="other">Other</option>
            </select>
            <textarea placeholder="Tell us about your distribution network..." class="md:col-span-2 bg-white/10 border border-white/20 rounded-xl px-4 py-3 text-white placeholder-gray-400 h-32 resize-none"></textarea>
            <button type="submit" class="md:col-span-2 bg-gradient-to-r from-emerald-500 to-blue-500 text-white px-8 py-4 rounded-xl font-medium hover:from-emerald-600 hover:to-blue-600 transition-all duration-300 transform hover:scale-105">
              Submit Partnership Inquiry
            </button>
          </form>
        </div>
      {/if}
      
      {#if activeTab === 'resources'}
        <!-- Trade Resources -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          {#each resources as resource}
            <div class="bg-white/10 backdrop-blur-md rounded-2xl p-6 border border-white/20 hover:bg-white/20 transition-all duration-300 group cursor-pointer">
              <div class="flex items-center justify-between">
                <div class="flex items-center space-x-4">
                  <div class="text-3xl">{resource.icon}</div>
                  <div>
                    <h4 class="text-lg font-medium text-white">{resource.name}</h4>
                    <p class="text-gray-400 text-sm">{resource.type} • {resource.size}</p>
                  </div>
                </div>
                <button class="bg-emerald-500 text-white px-4 py-2 rounded-lg hover:bg-emerald-600 transition-colors duration-300 group-hover:scale-105">
                  Download
                </button>
              </div>
            </div>
          {/each}
        </div>
      {/if}
      
      {#if activeTab === 'territories'}
        <!-- Available Territories -->
        <div class="space-y-6">
          {#each territories as territory}
            <div class="bg-white/10 backdrop-blur-md rounded-2xl p-6 border border-white/20 hover:bg-white/20 transition-all duration-300">
              <div class="flex items-center justify-between">
                <div>
                  <h4 class="text-2xl font-light text-white mb-2">{territory.name}</h4>
                  <p class="text-gray-400">{territory.markets}</p>
                </div>
                <div class="text-right">
                  <span class="inline-block px-4 py-2 rounded-full text-sm font-medium {territory.status === 'Active' ? 'bg-green-500/20 text-green-400' : territory.status === 'Expanding' ? 'bg-yellow-500/20 text-yellow-400' : 'bg-blue-500/20 text-blue-400'}">
                    {territory.status}
                  </span>
                </div>
              </div>
            </div>
          {/each}
        </div>
      {/if}
      
    </div>
    
  </div>
</section>
