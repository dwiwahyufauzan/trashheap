<script lang="ts">
    import { fly } from 'svelte/transition';

    let selectedFilter = $state('All');
    const filters = ['All', 'Mural', 'Skate', 'Music'];

    const items = [
        { id: 1, type: 'Mural', title: 'SS15 Wall Takeover', desc: '48-hour non-stop painting session in the back alleys.', size: 'large', img: 'https://i.pinimg.com/1200x/53/13/44/531344f39cd85390bce22c7520223c89.jpg', color: 'bg-gray-900' },
        { id: 2, type: 'Skate', title: 'Night Sessions', desc: 'After dark street cruising.', size: 'small', img: 'https://i.pinimg.com/1200x/ab/fc/cd/abfccddb071bc9deb8fcb8fab87e3f8b.jpg', color: 'bg-gray-900' },
        { id: 3, type: 'Music', title: 'Basement Gigs', desc: 'Loud noise in small spaces.', size: 'small', img: 'https://i.pinimg.com/1200x/cd/74/05/cd7405a8ef3535426e9e067e09581ab2.jpg', color: 'bg-gray-900' },
        { id: 4, type: 'Music', title: 'Campus Party', desc: 'A fun-filled event with music, food, and fun.', size: 'small', img: 'https://i.pinimg.com/736x/c6/51/7e/c6517ef999fde192d3646b81c57591ff.jpg', color: 'bg-gray-900' },
    ];

    let filteredItems = $derived(
        selectedFilter === 'All' ? items : items.filter(i => i.type === selectedFilter)
    );
</script>
<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous">
	<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400&family=JetBrains+Mono:wght@400;500&family=Syne:wght@400;700;800&display=swap" rel="stylesheet">
</svelte:head>

<section class="w-full max-w-[1440px] mx-auto px-4 sm:px-6 lg:px-12 py-12 md:py-16">
    <div class="flex flex-col lg:flex-row lg:items-end justify-between gap-8 mb-12 md:mb-20">
        <div class="space-y-4">
            <h2 class="text-gray-900 text-[15vw] font-syne md:text-[8rem] lg:text-[10rem] font-black uppercase tracking-tighter leading-[0.8]">
                LATEST<br/>
                <span class="text-orange-600 font-syne italic">DROPS</span>
            </h2>
            <div class="flex items-center gap-3">
                <div class="h-1 w-12 md:w-20 bg-gray-900"></div>
                <p class="text-gray-900 font-mono text-xs md:text-sm tracking-widest uppercase">Archive_V.01 // SBG_DSTRCT</p>
            </div>
            <p class="text-gray-700 text-xs md:text-base max-w-lg leading-relaxed mt-2">
                Temukan aktivitas terbaru dari komunitas Subang: mural, skate, gigs, dan kolaborasi kreatif lainnya. Pilih kategori untuk menelusuri koleksi event dan karya yang sudah berlangsung maupun yang akan datang.
            </p>
        </div>
    </div>

    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 md:gap-6 auto-rows-[300px] md:auto-rows-[350px]">
        {#each filteredItems as item (item.id)}
            <div 
                in:fly={{ y: 20, duration: 400 }}
                class="group relative overflow-hidden bg-zinc-900 border-2 border-white transition-all rounded-2xl duration-500
                {selectedFilter === 'All' && item.size === 'large' ? 'sm:col-span-2 sm:row-span-2' : 'col-span-1'}"
            >
                <div class="absolute inset-0 z-0">
                    <img 
                        src={item.img} 
                        alt={item.title}
                        class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 opacity-50 group-hover:opacity-100 scale-105 group-hover:scale-100"
                    />
                    <div class="absolute inset-0 {item.color} mix-blend-multiply opacity-20 md:opacity-0 md:group-hover:opacity-40 transition-opacity"></div>
                </div>

                <div class="absolute inset-0 z-10 p-3 md:p-6 flex flex-col justify-between">
                    <div class="flex justify-between items-start">
                        <span class="bg-white text-black px-2 py-1 text-[6px] md:text-[10px] font-black uppercase tracking-tighter">
                            {item.type}
                        </span>
                        <div class="w-8 h-8 md:w-9 md:h-9 bg-white text-black flex items-center justify-center -rotate-12 group-hover:rotate-0 transition-transform duration-300">
                            <span class="material-symbols-outlined font-black text-base md:text-lg">north_east</span>
                        </div>
                    </div>
                    
                    <div class="bg-white p-3 md:p-5 group-hover:bg-orange-600 transition-colors duration-300 transform translate-y-2 group-hover:translate-y-0 shadow-[4px_4px_0px_0px_rgba(0,0,0,1)]">
                        <h3 class="text-black group-hover:text-white text-xs md:text-base lg:text-lg font-black uppercase leading-none tracking-tighter font-inter" style="font-family: 'Inter', sans-serif;">
                            {item.title}
                        </h3>
                        {#if item.desc}
                            <p class="text-black group-hover:text-white mt-1.5 text-[8px] md:text-[9px] font-bold leading-tight uppercase opacity-100 md:opacity-0 md:group-hover:opacity-100 transition-opacity font-inter" style="font-family: 'Inter', sans-serif;">
                                {item.desc}
                            </p>
                        {/if}
                    </div>
                </div>
            </div>
        {/each}

        <button class="bg-white border-2 border-gray-900 flex flex-col items-center justify-center p-4 md:p-6 transition-all hover:bg-gray-200 hover:border-gray-900 group rounded-2xl">
            <div class="w-12 h-12 md:w-14 md:h-14 rounded-full border-3 md:border-4 border-black flex items-center justify-center mb-3 group-hover:rotate-90 transition-transform">
                <span class="text-black *: text-2xl md:text-3xl font-black">+</span>
            </div>
            <span class="text-black font-black uppercase tracking-[0.2em] text-[9px]">Explore_Full_Archive</span>
        </button>
    </div>
</section>

<style>
    /* Hide scrollbar for Chrome, Safari and Opera */
    .no-scrollbar::-webkit-scrollbar {
        display: none;
    }

    /* Hide scrollbar for IE, Edge and Firefox */
    .no-scrollbar {
        -ms-overflow-style: none;  /* IE and Edge */
        scrollbar-width: none;  /* Firefox */
    }

    h2, h3 {
        font-family: 'Syne', 'Inter', 'Impact', sans-serif;
    }
</style>