<script lang="ts">
    const announcements = [
        "New Merch Drop Available",
        "Next Wall Jam: Oct 24",
        "Underground Sessions Vol. 4 Out Now",
        "Support Local Scene",
        "SBG Collective Worldwide"
    ];
</script>

<div class="relative bg-white border-y-2 border-black py-4 overflow-hidden group cursor-pointer">
    <div class="absolute inset-y-0 left-0 w-20 bg-gradient-to-r from-orange-600 to-transparent z-10"></div>
    <div class="absolute inset-y-0 right-0 w-20 bg-gradient-to-l from-orange-600 to-transparent z-10"></div>

    <div class="flex whitespace-nowrap group-hover:pause-animation animate-marquee">
        {#each [1, 2] as _}
            <div class="flex items-center gap-12 px-6">
                {#each announcements as text}
                    <div class="flex items-center gap-8">
                        <span class="text-black text-xl md:text-2xl font-black uppercase tracking-tighter italic">
                            {text}
                        </span>
                        <div class="w-3 h-3 bg-black rotate-45 group-hover:bg-orange-600 transition-colors duration-500"></div>
                        
                        <span class="text-transparent font-black uppercase tracking-tighter italic text-xl md:text-2xl" 
                              style="-webkit-text-stroke: 1.5px black;">
                            SBG_DSTRCT
                        </span>
					</div>
                        
                    <div class="w-3 h-3 bg-black rotate-45 group-hover:bg-orange-600 transition-colors duration-500"></div>
                    {/each}
                </div>
            {/each}
        </div>  
    </div>


<style>
    @keyframes marquee {
        0% { transform: translateX(0); }
        100% { transform: translateX(-50%); }
    }

    .animate-marquee {
        display: inline-flex;
        animation: marquee 30s linear infinite;
    }

    .group-hover\:pause-animation:hover {
        animation-play-state: paused;
    }

    /* Modern Italic Typography feeling */
    span {
        font-family: 'Inter', 'Syncopate', sans-serif;
    }
</style>