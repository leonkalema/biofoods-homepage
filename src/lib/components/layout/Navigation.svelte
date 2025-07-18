<script lang="ts">
  export let logoSrc: string = "/bio-logo-no-strapline-2020.png";
</script>

<nav class="relative z-50 flex items-center justify-between px-6 py-6 lg:px-12">
  <div class="flex items-center space-x-2">
    <img src={logoSrc} alt="Bio Foods" class="h-12 w-auto" />
  </div>
  
  <div class="hidden md:flex items-center space-x-8 text-gray-700 font-medium">
    <a href="#products" class="hover:text-green-600 transition-colors duration-300">Products</a>
    <a href="#bio-way" class="hover:text-green-600 transition-colors duration-300">Bio Way</a>
    <a href="#sustainability" class="hover:text-green-600 transition-colors duration-300">Sustainability</a>
    <a href="#about" class="hover:text-green-600 transition-colors duration-300">About</a>
    <button class="bg-green-600 text-white px-6 py-2 rounded-full hover:bg-green-700 transition-all duration-300 transform hover:scale-105">
      Shop Now
    </button>
  </div>
  
  <!-- Mobile Menu Button -->
  <button class="md:hidden p-2" aria-label="Open mobile menu">
    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
    </svg>
  </button>
</nav>
