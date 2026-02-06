<script lang="ts">
    // Menggunakan Runes (Svelte 5)
    let email = $state('');

    function handleSubmit(e: Event) {
        e.preventDefault();
        console.log('Newsletter subscription:', email);
        email = '';
    }
</script>

<section class="relative bg-orange-600 border-y-4 border-black overflow-hidden group">
    <div class="absolute inset-0 flex items-center overflow-hidden opacity-10 pointer-events-none select-none">
        <div class="text-[20rem] font-black uppercase whitespace-nowrap animate-marquee leading-none">
            JOIN THE CULT JOIN THE CULT JOIN THE CULT
        </div>
    </div>

    <div class="relative z-10 max-w-7xl mx-auto flex flex-col lg:flex-row items-center justify-between gap-12 px-8 py-12 md:py-16 mt-0">
        
        <div class="text-left space-y-4 max-w-xl">
            <div class="inline-block bg-black text-white px-3 py-1 text-xs font-black uppercase tracking-[0.3em]">
                Newsletter_v.01
            </div>
            <h2 class="text-black text-6xl md:text-7xl font-black uppercase leading-[0.85] tracking-tighter">
                DON'T MISS <br/> 
                <span class="text-white drop-shadow-[4px_4px_0px_#000]">THE CHAOS.</span>
            </h2>
            <p class="text-black/80 font-bold max-w-sm leading-tight text-lg">
                Get the latest drops, gig updates, and street reports straight to your inbox.
            </p>
        </div>

        <form 
            onsubmit={handleSubmit} 
            class="relative w-full max-w-lg bg-black p-2 shadow-[12px_12px_0px_0px_rgba(0,0,0,0.2)] group-hover:shadow-[12px_12px_0px_0px_rgba(255,255,255,1)] transition-all duration-500"
        >
            <div class="flex flex-col sm:flex-row gap-0">
                <div class="relative flex-grow">
                    <span class="absolute left-4 top-1/2 -translate-y-1/2 text-black/30 font-black italic">@</span>
                    <input 
                        bind:value={email}
                        class="w-full bg-white px-10 py-5 text-black font-black placeholder-black/30 focus:outline-none uppercase text-lg" 
                        placeholder="ENTER YOUR MAIL" 
                        type="email"
                        required
                    />
                </div>
                <button 
                    type="submit"
                    class="bg-white border-l-2 border-black sm:border-l-4 px-8 py-5 text-black font-black uppercase tracking-tighter hover:bg-black hover:text-orange-600 transition-all active:scale-95 duration-200"
                >
                    SUBMIT_NOW
                </button>
            </div>
            
            <div class="absolute -bottom-6 left-0 flex gap-2">
                <div class="h-2 w-12 bg-black"></div>
                <div class="h-2 w-2 bg-black"></div>
                <div class="h-2 w-2 bg-black"></div>
            </div>
        </form>
    </div>
</section>

<style>
    @keyframes marquee {
        0% { transform: translateX(0); }
        100% { transform: translateX(-50%); }
    }

    .animate-marquee {
        animation: marquee 20s linear infinite;
    }

    /* Memastikan font terasa berat dan solid */
    h2 {
        font-family: 'Inter', 'Impact', sans-serif;
    }
</style>