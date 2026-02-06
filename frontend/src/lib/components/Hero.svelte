    <script lang="ts">
        import { onMount } from 'svelte';
        
        let mounted = $state(false);
        
        onMount(() => {
            mounted = true;
        });
    </script>

    <svelte:head>
        <link rel="preconnect" href="https://fonts.googleapis.com">
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous">
        <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
    </svelte:head>

    <section class="relative w-full min-h-screen bg-[#080808] flex items-center justify-center overflow-hidden px-4 md:px-8 py-16 md:py-20">
        
        <!-- Noise Texture -->
        <div class="fixed inset-0 opacity-[0.03] pointer-events-none z-0 mix-blend-overlay" 
            style="background-image: url('https://grainy-gradients.vercel.app/noise.svg');">
        </div>

        <!-- Background Image -->
        <div class="absolute inset-0 z-0">
            <img 
                src="https://i.pinimg.com/736x/23/55/7b/23557b950b0ac1e661529bbdb741b17e.jpg" 
                alt="Subang Street" 
                class="w-full h-full object-cover brightness-[0.3] grayscale"
            />
            <div class="absolute inset-0 bg-gradient-to-b from-black/50 via-transparent to-black/80"></div>
        </div>

        <!-- Main Content -->
        <div class="relative z-10 max-w-7xl mx-auto w-full">
            
            <!-- Top Label -->
            <div class="mb-8 md:mb-12">
                <div class="inline-flex items-center gap-3 border-l-4 border-orange-600 pl-4">
                    <span class="w-2 h-2 bg-orange-600 rounded-full animate-pulse"></span>
                    <span class="font-mono text-[10px] md:text-xs text-orange-600 uppercase tracking-widest font-bold">● Est. 2023 // Live</span>
                </div>
            </div>

            <!-- Main Heading -->
            <div class="mb-8 md:mb-12">
                <h1 class="font-['Syne'] font-black uppercase tracking-tighter leading-[0.8] text-white">
                    <span class="block text-5xl md:text-8xl lg:text-9xl mb-2 md:mb-4 {mounted ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'} transition-all duration-700">
                        THROW IT
                    </span>
                    <span class="block text-6xl md:text-8xl lg:text-[6rem] text-orange-600 {mounted ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'} transition-all duration-700 delay-100">
                        AWAY HERE
                    </span>
                </h1>
                
                <div class="flex items-center gap-4 mt-6 md:mt-8 {mounted ? 'opacity-100 translate-x-0' : 'opacity-0 -translate-x-10'} transition-all duration-700 delay-200">
                    <div class="h-1 w-16 md:w-24 bg-white"></div>
                    <p class="font-mono text-[10px] md:text-xs text-gray-500 uppercase tracking-widest">TRASHHEAP_ARCHIVE_V01</p>
                </div>
            </div>

            <!-- Description -->
            <div class="max-w-2xl mb-12 md:mb-16 {mounted ? 'opacity-100' : 'opacity-0'} transition-all duration-700 delay-300">
                <p class="text-gray-400 text-sm md:text-lg leading-relaxed">
                    A decentralized collective of <span class="text-white font-bold">artists, musicians, and skaters</span>. 
                    We paint walls, make noise, and ride streets. The underground heartbeat of Subang's creative rebellion.
                </p>
            </div>

            <!-- CTA Buttons -->
            <div class="flex flex-col sm:flex-row gap-4 {mounted ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'} transition-all duration-700 delay-400">
                <button class="group relative px-8 py-4 bg-orange-600 text-white font-black uppercase text-xs md:text-sm tracking-widest hover:bg-white hover:text-orange-600 transition-all duration-300 overflow-hidden">
                    <span class="relative z-10">Join The Movement</span>
                    <div class="absolute inset-0 bg-white transform translate-y-full group-hover:translate-y-0 transition-transform duration-300"></div>
                    <span class="absolute top-0 right-0 w-3 h-3 bg-black -mt-1 -mr-1"></span>
                    <span class="absolute bottom-0 left-0 w-3 h-3 bg-black -mb-1 -ml-1"></span>
                </button>
                
                <button class="group px-8 py-4 bg-transparent border-2 border-white text-white font-black uppercase text-xs md:text-sm tracking-widest hover:bg-white hover:text-black transition-all duration-300">
                    Watch Showreel
                    <span class="inline-block ml-2 group-hover:translate-x-1 transition-transform">→</span>
                </button>
            </div>
        </div>

        <!-- Border Bottom -->
        <div class="absolute bottom-0 left-0 right-0 h-2 md:h-3 bg-orange-600"></div>
    </section>

    <style>
        :global(body) {
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }
    </style>