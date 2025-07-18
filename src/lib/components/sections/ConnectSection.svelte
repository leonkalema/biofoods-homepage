<script lang="ts">
  import { onMount } from 'svelte';
  import { browser } from '$app/environment';
  
  let sectionElement: HTMLElement;
  let isVisible = false;
  let selectedAudience: 'consumer' | 'business' | 'media' = 'consumer';
  
  const contactOptions = {
    consumer: {
      title: 'For Consumers',
      subtitle: 'Questions about our products?',
      contacts: [
        { type: 'Customer Care', value: '+254 700 123 456', icon: '📞' },
        { type: 'Email Support', value: 'hello@biofoods.co.ke', icon: '✉️' },
        { type: 'WhatsApp', value: '+254 700 123 456', icon: '💬' }
      ]
    },
    business: {
      title: 'For Business',
      subtitle: 'Partnership & Trade Inquiries',
      contacts: [
        { type: 'Business Development', value: 'trade@biofoods.co.ke', icon: '🤝' },
        { type: 'Export Inquiries', value: 'export@biofoods.co.ke', icon: '🌍' },
        { type: 'Procurement', value: 'm.nyagaya@biofoods.co.ke', icon: '📋' }
      ]
    },
    media: {
      title: 'For Media',
      subtitle: 'Press & Media Relations',
      contacts: [
        { type: 'Press Inquiries', value: 'media@biofoods.co.ke', icon: '📰' },
        { type: 'Brand Partnerships', value: 'partnerships@biofoods.co.ke', icon: '🎯' },
        { type: 'Sustainability Stories', value: 'sustainability@biofoods.co.ke', icon: '🌱' }
      ]
    }
  };
  
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

<section bind:this={sectionElement} class="relative min-h-screen bg-gradient-to-br from-gray-900 via-slate-800 to-gray-900 text-white overflow-hidden">
  
  <!-- Animated Background -->
  <div class="absolute inset-0 pointer-events-none">
    <div class="absolute top-0 left-0 w-full h-full opacity-20">
      <div class="absolute top-20 left-20 w-64 h-64 bg-gradient-to-br from-emerald-400 to-green-500 rounded-full blur-3xl animate-pulse"></div>
      <div class="absolute bottom-20 right-20 w-80 h-80 bg-gradient-to-br from-blue-400 to-cyan-500 rounded-full blur-3xl animate-pulse" style="animation-delay: 2s;"></div>
      <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-96 h-96 bg-gradient-to-br from-purple-400 to-pink-500 rounded-full blur-3xl animate-pulse" style="animation-delay: 4s;"></div>
    </div>
  </div>
  
  <div class="relative z-10 max-w-7xl mx-auto px-6 lg:px-12 py-20">
    
    <!-- Section Header -->
    <div class="text-center mb-16">
      <div 
        class="transition-all duration-1000 ease-out {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}"
        style="transition-delay: 200ms;"
      >
        <h2 class="text-6xl lg:text-8xl font-extralight mb-6">
          Connect
          <span class="bg-gradient-to-r from-emerald-400 to-blue-400 bg-clip-text text-transparent">
            With Us
          </span>
        </h2>
        <p class="text-xl lg:text-2xl text-gray-300 font-light max-w-3xl mx-auto">
          Ready to join the Bio Foods journey? We're here to help with all your needs
        </p>
      </div>
    </div>
    
    <!-- Audience Selector -->
    <div class="flex justify-center mb-12">
      <div class="bg-white/10 backdrop-blur-md rounded-2xl p-2 border border-white/20">
        <button 
          class="px-6 py-3 rounded-xl transition-all duration-300 {selectedAudience === 'consumer' ? 'bg-emerald-500 text-white' : 'text-gray-300 hover:text-white'}"
          on:click={() => selectedAudience = 'consumer'}
        >
          Consumers
        </button>
        <button 
          class="px-6 py-3 rounded-xl transition-all duration-300 {selectedAudience === 'business' ? 'bg-emerald-500 text-white' : 'text-gray-300 hover:text-white'}"
          on:click={() => selectedAudience = 'business'}
        >
          Business
        </button>
        <button 
          class="px-6 py-3 rounded-xl transition-all duration-300 {selectedAudience === 'media' ? 'bg-emerald-500 text-white' : 'text-gray-300 hover:text-white'}"
          on:click={() => selectedAudience = 'media'}
        >
          Media
        </button>
      </div>
    </div>
    
    <!-- Contact Information -->
    <div class="max-w-4xl mx-auto">
      <div class="text-center mb-12">
        <h3 class="text-4xl font-light mb-4">{contactOptions[selectedAudience as keyof typeof contactOptions].title}</h3>
        <p class="text-xl text-gray-400">{contactOptions[selectedAudience as keyof typeof contactOptions].subtitle}</p>
      </div>
      
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mb-16">
        {#each contactOptions[selectedAudience as keyof typeof contactOptions].contacts as contact, index}
          <div 
            class="group transition-all duration-700 ease-out {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}"
            style="transition-delay: {600 + index * 200}ms;"
          >
            <div class="relative">
              <!-- Contact Glow -->
              <div class="absolute -inset-4 bg-gradient-to-br from-emerald-400/20 to-blue-400/20 rounded-3xl opacity-0 group-hover:opacity-40 transition-all duration-700 filter blur-xl"></div>
              
              <!-- Contact Card -->
              <div class="relative bg-white/10 backdrop-blur-md rounded-3xl p-8 border border-white/20 hover:bg-white/20 transition-all duration-700 hover:scale-105 hover:-translate-y-2 text-center">
                <div class="text-4xl mb-4 group-hover:scale-110 transition-transform duration-500">
                  {contact.icon}
                </div>
                <h4 class="text-xl font-medium text-white mb-2">{contact.type}</h4>
                <p class="text-emerald-400 font-medium">{contact.value}</p>
              </div>
            </div>
          </div>
        {/each}
      </div>
    </div>
    
    <!-- Newsletter Signup -->
    <div class="max-w-2xl mx-auto">
      <div 
        class="bg-white/10 backdrop-blur-md rounded-3xl p-8 border border-white/20 text-center transition-all duration-1000 ease-out {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}"
        style="transition-delay: 1200ms;"
      >
        <h3 class="text-3xl font-light mb-4">Stay Updated</h3>
        <p class="text-gray-400 mb-6">Get the latest news, product launches, and sustainability updates</p>
        <div class="flex flex-col sm:flex-row gap-4">
          <input 
            type="email" 
            placeholder="Enter your email address" 
            class="flex-1 bg-white/10 border border-white/20 rounded-xl px-4 py-3 text-white placeholder-gray-400"
          >
          <button class="bg-gradient-to-r from-emerald-500 to-blue-500 text-white px-8 py-3 rounded-xl font-medium hover:from-emerald-600 hover:to-blue-600 transition-all duration-300 transform hover:scale-105">
            Subscribe
          </button>
        </div>
      </div>
    </div>
    
    <!-- Social Links -->
    <div class="text-center mt-16">
      <div 
        class="transition-all duration-1000 ease-out {isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}"
        style="transition-delay: 1400ms;"
      >
        <p class="text-gray-400 mb-6">Follow our journey</p>
        <div class="flex justify-center space-x-6">
          <a href="https://facebook.com/biofoods" class="w-12 h-12 bg-white/10 rounded-full flex items-center justify-center hover:bg-white/20 transition-all duration-300 hover:scale-110">
            <span class="text-xl">📘</span>
          </a>
          <a href="https://instagram.com/biofoods" class="w-12 h-12 bg-white/10 rounded-full flex items-center justify-center hover:bg-white/20 transition-all duration-300 hover:scale-110">
            <span class="text-xl">📷</span>
          </a>
          <a href="https://twitter.com/biofoods" class="w-12 h-12 bg-white/10 rounded-full flex items-center justify-center hover:bg-white/20 transition-all duration-300 hover:scale-110">
            <span class="text-xl">🐦</span>
          </a>
          <a href="https://linkedin.com/company/biofoods" class="w-12 h-12 bg-white/10 rounded-full flex items-center justify-center hover:bg-white/20 transition-all duration-300 hover:scale-110">
            <span class="text-xl">💼</span>
          </a>
        </div>
      </div>
    </div>
    
  </div>
</section>
