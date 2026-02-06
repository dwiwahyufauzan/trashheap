<script lang="ts">
    import { fly } from 'svelte/transition';
    import merch1 from '$lib/assets/merch/merch1.png';
    import merch2 from '$lib/assets/merch/merch2.png';
    import merch3 from '$lib/assets/merch/merch3.png';

    const merchItems = [
        { 
            id: 1, 
            name: 'Collective Tee', 
            type: 'APPAREL',
            price: '150K', 
            stock: 'Limited',
            img: merch1,
            desc: 'Premium cotton, sablon tebal, desain eksklusif.'
        },
        { 
            id: 2, 
            name: 'Sticker Pack', 
            type: 'ACCESSORIES',
            price: '30K', 
            stock: 'In Stock',
            img: merch2,
            desc: '10 sticker vinyl anti air, desain original.'
        },
        { 
            id: 3, 
            name: 'Tote Bag', 
            type: 'ACCESSORIES',
            price: '80K', 
            stock: 'Limited',
            img: merch3,
            desc: 'Canvas tebal, sablon 2 sisi, eco-friendly.'
        },
        { 
            id: 4, 
            name: 'Hoodie Black', 
            type: 'APPAREL',
            price: '250K', 
            stock: 'Pre-Order',
            img: 'https://i.pinimg.com/736x/c6/51/7e/c6517ef999fde192d3646b81c57591ff.jpg',
            desc: 'Fleece premium, hoodie tebal, limited edition.'
        },
        { 
            id: 5, 
            name: 'Embroidery Cap', 
            type: 'ACCESSORIES',
            price: '120K', 
            stock: 'In Stock',
            img: 'https://i.pinimg.com/736x/ab/fc/cd/abfccddb071bc9deb8fcb8fab87e3f8b.jpg',
            desc: 'Bordir halus, adjustable strap, unisex.'
        },
    ];

    const stackedItems = merchItems.slice(0, 3);
</script>

<svelte:head>
    <link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=JetBrains+Mono:wght@500&display=swap" rel="stylesheet">
</svelte:head>

<section class="w-full bg-white px-4 py-10 md:py-8 overflow-visible">
    <div class="max-w-[1440px] mx-auto">
        
        <div class="flex flex-col lg:flex-row items-start lg:items-end justify-between gap-6 mb-10 md:mb-16">
            <div class="max-w-3xl">
                <h2 class="text-black text-[12vw] md:text-[5rem] lg:text-[7rem] font-syne font-black uppercase tracking-tighter leading-[0.85]">
                    OFFICIAL<br/>
                    <span class="text-orange-600 italic">MERCH</span>
                </h2>
                <p class="text-gray-700 text-xs md:text-base max-w-lg leading-relaxed mt-2 mb-2">
                    Dapatkan produk original SBG Collective untuk mendukung gerakan kreatif Subang. Semua merch dibuat dengan kualitas premium dan desain eksklusif.
                </p>
                <div class="flex items-center gap-3 mt-6">
                    <div class="h-[2px] w-12 bg-black"></div>
                    <p class="font-mono text-[10px] md:text-sm tracking-widest uppercase">STREET_ARCHIVE // VOL. 01</p>
                </div>
            </div>

            <div class="hidden lg:flex relative h-[420px] w-[420px] items-start justify-center -mt-12">
                {#each stackedItems as item, i}
                    <div 
                        class="absolute transition-all duration-500 hover:z-50 hover:scale-110"
                        style="transform: translateY({i * 50}px) rotate({i === 0 ? -8 : i === 1 ? 4 : -2}deg) translateX({i * 10}px);"
                    >
                        <div class="w-[400px] h-[300px] bg-transparent overflow-visible">
                            <img src={item.img} alt={item.name} class="w-full h-full object-contain transition-all duration-300" />
                        </div>
                    </div>
                {/each}
            </div>
        </div>

        <div class="grid grid-cols-2 lg:grid-cols-3 gap-3 md:gap-6">
            {#each merchItems.slice(0, 3) as item (item.id)}
                <div 
                    in:fly={{ y: 20, duration: 400 }}
                    class="group relative flex flex-col bg-zinc-100 border-2 border-black transition-all hover:shadow-[4px_4px_0px_0px_rgba(0,0,0,1)] md:hover:shadow-[8px_8px_0px_0px_rgba(0,0,0,1)]"
                >
                    <div class="relative aspect-square md:aspect-[4/5] overflow-hidden border-b-2 border-black bg-white flex items-center justify-center p-4 md:p-6">
                        <img 
                            src={item.img} 
                            alt={item.name}
                            class="max-w-[100%] max-h-[100%] object-contain transition-all duration-500"
                        />
                        <div class="absolute top-2 left-2 flex flex-col gap-1">
                            <span class="bg-black text-white px-1.5 py-0.5 text-[7px] md:text-[10px] font-bold uppercase tracking-tighter self-start">
                                {item.type}
                            </span>
                        </div>
                        <div class="absolute top-2 right-2">
                             <span class="bg-orange-600 text-white px-1.5 py-0.5 text-[7px] md:text-[10px] font-bold uppercase">
                                {item.stock}
                            </span>
                        </div>
                    </div>

                    <div class="p-3 md:p-5 bg-white flex-1 flex flex-col justify-between group-hover:bg-orange-600 transition-colors duration-300">
                        <div>
                            <h3 class="text-black group-hover:text-white text-xs md:text-xl font-black uppercase leading-none tracking-tighter mb-1 font-syne">
                                {item.name}
                            </h3>
                        </div>
                        
                        <p class="hidden md:block text-black group-hover:text-white text-[10px] leading-tight uppercase opacity-70">
                            {item.desc}
                        </p>

                        <button class="mt-2 w-full py-1.5 border border-black bg-black text-white group-hover:bg-white group-hover:text-black text-[9px] md:text-xs font-bold uppercase transition-all">
                            available
                        </button>
                    </div>
                </div>
            {/each}
        </div>
    </div>
</section>

<style>
    :global(body) {
        overflow-x: hidden;
    }
    .font-syne { font-family: 'Syne', sans-serif; }
</style>