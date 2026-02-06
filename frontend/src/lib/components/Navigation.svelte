<script lang="ts">
    import { onMount } from 'svelte';
    import { fade, slide, fly } from 'svelte/transition';
    import { quintOut } from 'svelte/easing';
    import logo from '$lib/assets/logo.png';

    let mobileMenuOpen = false;
    let scrolled = false;

    // Kunci scroll body saat menu mobile terbuka
    $: if (typeof document !== 'undefined') {
        document.body.style.overflow = mobileMenuOpen ? 'hidden' : 'auto';
    }

    function toggleMobileMenu() {
        mobileMenuOpen = !mobileMenuOpen;
    }

    onMount(() => {
        const handleScroll = () => {
            scrolled = window.scrollY > 20;
        };
        window.addEventListener('scroll', handleScroll);
        return () => window.removeEventListener('scroll', handleScroll);
    });
</script>

<nav 
    class="fixed top-0 w-full z-50 transition-all duration-300 border-b 
    {scrolled ? 'bg-black border-white/20 py-3 shadow-[0_4px_30px_rgba(0,0,0,0.5)]' : 'bg-transparent border-transparent py-5'}"
>
    <div class="max-w-7xl mx-auto px-4 md:px-8 flex items-center justify-between">
        
        <div class="flex items-center gap-4 group cursor-pointer">
            <div class="flex flex-col">
                <h2 class="text-white text-2xl font-black tracking-tighter uppercase leading-none italic">
                    TRASH<span class="text-orange-500">HEAP</span>
                </h2>
            </div>
        </div>

        <div class="hidden md:flex items-center gap-10">
            <div class="flex items-center gap-8">
                {#each ['Home', 'Activities', 'News', 'Events', 'Merch'] as item}
                    <a 
                        href="/{item.toLowerCase() === 'home' ? '' : item.toLowerCase()}" 
                        class="relative group text-white font-bold uppercase text-sm tracking-wider overflow-hidden py-1"
                    >
                        <span class="relative z-10 transition-colors duration-300 group-hover:text-black">{item}</span>
                        <span class="absolute bottom-0 left-0 w-full h-0 bg-white group-hover:h-full transition-all duration-300 ease-out"></span>
                    </a>
                {/each}
            </div>
        </div>

        <button 
            type="button"
            class="relative z-50 md:hidden w-8 h-8 flex items-center justify-center group" 
            onclick={toggleMobileMenu}
            aria-label={mobileMenuOpen ? 'Close menu' : 'Open menu'}
            aria-expanded={mobileMenuOpen}
        >
            {#if mobileMenuOpen}
                <!-- Icon X -->
                <div class="relative w-8 h-8 flex items-center justify-center">
                    <span class="absolute h-0.5 w-8 bg-white rotate-45"></span>
                    <span class="absolute h-0.5 w-8 bg-white -rotate-45"></span>
                </div>
            {:else}
                <!-- Icon Hamburger -->
                <div class="flex flex-col items-end gap-1.5 w-full">
                    <span class="h-0.5 w-8 bg-white transition-all duration-300"></span>
                    <span class="h-0.5 w-6 bg-orange-500 transition-all duration-300 group-hover:w-8"></span>
                    <span class="h-0.5 w-4 bg-white transition-all duration-300 group-hover:w-8"></span>
                </div>
            {/if}
        </button>
    </div>
</nav>

{#if mobileMenuOpen}
    <div 
        class="fixed inset-0 bg-black z-40 flex flex-col justify-center px-8"
        transition:fade={{ duration: 200 }}
    >
        <div class="absolute right-0 top-0 opacity-10 pointer-events-none overflow-hidden h-full flex items-center">
            <h1 class="text-[40vh] font-black text-white leading-none whitespace-nowrap rotate-90 origin-center">
                CULTURE
            </h1>
        </div>

        <div class="flex flex-col gap-2 relative z-10">
            {#each ['Home', 'Activities', 'News', 'Events', 'Merch'] as item, i}
                <a 
                    href="/{item.toLowerCase() === 'home' ? '' : item.toLowerCase()}" 
                    class="text-5xl sm:text-7xl font-black text-transparent text-stroke-white hover:text-orange-500 hover:text-stroke-orange transition-all duration-300 uppercase tracking-tighter"
                    in:fly={{ y: 50, duration: 400, delay: 100 + (i * 50), easing: quintOut }}
                    onclick={toggleMobileMenu}
                >
                    {item}<span class="text-lg align-top text-white/50 ml-2">0{i+1}</span>
                </a>
            {/each}
        </div>

        <div 
            class="mt-12 w-full border-t border-white/20 pt-8 flex flex-col gap-4"
            in:fade={{ delay: 400 }}
        >
        </div>
    </div>
{/if}

<style>
    /* Utility class untuk teks outline (stroke) */
    .text-stroke-white {
        -webkit-text-stroke: 1px white;
    }
    .text-stroke-orange {
        -webkit-text-stroke: 1px #ea580c; /* orange-600 */
        -webkit-text-stroke-width: 0px;
        color: #ea580c;
    }
    
    /* Mengembalikan warna solid saat hover pada mobile */
    a:hover.text-stroke-white {
        -webkit-text-stroke: 0px;
    }
</style>