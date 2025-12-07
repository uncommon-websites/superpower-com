<script lang="ts">
  import { onMount } from 'svelte';

  let isScrolled = false;

  onMount(() => {
    const handleScroll = () => {
      isScrolled = window.scrollY > 50;
    };
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  });
</script>

<header class="fixed top-0 left-0 right-0 z-50 transition-all duration-300 {isScrolled ? 'bg-white/90 backdrop-blur-md py-4 shadow-sm' : 'bg-transparent py-6'}">
  <div class="max-w-[1400px] mx-auto px-6 flex items-center justify-between">
    <!-- Logo -->
    <a href="/" class="text-2xl font-bold tracking-tight {isScrolled ? 'text-black' : 'text-white'}">
      superpower
    </a>

    <!-- Navigation -->
    <nav class="hidden md:flex items-center gap-8">
      {#each ['How it Works', 'What We Test', 'Reviews', 'FAQs', 'Our Why'] as item}
        <a href="#{item.toLowerCase().replace(/ /g, '-')}" class="text-sm font-medium hover:opacity-70 transition-opacity {isScrolled ? 'text-gray-900' : 'text-white/90'}">
          {item}
        </a>
      {/each}
    </nav>

    <!-- Actions -->
    <div class="flex items-center gap-4">
      <a href="/login" class="text-sm font-medium hover:opacity-70 transition-opacity {isScrolled ? 'text-gray-900' : 'text-white'}">
        Login
      </a>
      <a href="/join" class="bg-brand-orange hover:bg-brand-orange-hover text-white text-sm font-medium px-5 py-2.5 rounded-full transition-colors">
        Try Superpower
      </a>
    </div>
  </div>
</header>
