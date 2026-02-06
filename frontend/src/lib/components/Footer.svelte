<script lang="ts">
    import logo from '$lib/assets/logo.png';
</script>

<footer class="bg-black border-t-[12px] border-orange-600 pt-24 pb-12 overflow-hidden rounded-t-4xl">
    <div class="max-w-[1400px] mx-auto px-6">
        
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-16 mb-24">
            
            <div class="lg:col-span-6 space-y-8">
                <div class="flex items-center gap-4">
                    <div class="w-16 h-16 flex items-center justify-center">
                        <img src={logo} alt="TRASHHEAP Logo" class="w-full h-full object-contain" />
                    </div>
                    <p class="text-white text-xl font-bold leading-tight max-w-md uppercase tracking-tight">
                        TRASHHEAP
                    </p>
                </div>
                <p class="text-zinc-500 text-xl font-bold leading-tight max-w-md uppercase tracking-tight">
                    A decentralized collective of artists, musicians, and skaters. 
                    <span class="text-white">A community-driven project.</span>
                </p>
                
                <div class="flex gap-2">
                    {#each ['IG', 'TW', 'YT', 'BC'] as social}
                        <a href="/" class="w-12 h-12 border-2 border-zinc-800 flex items-center justify-center text-[10px] font-black text-zinc-500 hover:bg-white hover:text-black hover:border-white transition-all duration-300">
                            {social}
                        </a>
                    {/each}
                </div>
            </div>

            <div class="lg:col-span-3 space-y-6">
                <h3 class="text-orange-600 text-xs font-black uppercase tracking-[0.3em] mb-8 flex items-center gap-2">
                    <span class="w-2 h-2 bg-orange-600"></span> Explore_Index
                </h3>
                <nav class="flex flex-col gap-4">
                    {#each ['Activities', 'News', 'Events', 'Merch'] as link}
                        <a href="/" class="text-zinc-400 text-lg font-bold uppercase hover:text-white hover:translate-x-2 transition-all duration-300 flex items-center justify-between group">
                            {link}
                            <span class="material-symbols-outlined opacity-100 md:opacity-0 md:group-hover:opacity-100 text-orange-600 transition-opacity">arrow_forward</span>
                        </a>
                    {/each}
                </nav>
            </div>

            <div class="lg:col-span-3 space-y-6">
                <h3 class="text-orange-600 text-xs font-black uppercase tracking-[0.3em] mb-8 flex items-center gap-2">
                    <span class="w-2 h-2 bg-orange-600"></span> Headquarters
                </h3>
                <div class="text-zinc-400 space-y-4">
                    <div class="group cursor-pointer">
                        <p class="text-[10px] text-zinc-600 font-black uppercase mb-1">Physical_Address</p>
                        <p class="text-white font-bold uppercase group-hover:text-orange-600 transition-colors italic">Subang, West Java, ID</p>
                    </div>
                    <div class="group cursor-pointer">
                        <p class="text-[10px] text-zinc-600 font-black uppercase mb-1">Digital_Signal</p>
                        <p class="text-white font-bold uppercase group-hover:text-orange-600 transition-colors italic">trashheap@gmail.com</p>
                    </div>
                </div>
            </div>
        </div>

        <div class="pt-8 border-t border-zinc-900 flex flex-col md:flex-row justify-between items-center gap-6">
            <div class="flex items-center gap-4">
                <p class="text-[10px] font-mono text-zinc-600 uppercase">© 2026 TRASHHEAP // All Rights Reserved</p>
                <span class="h-1 w-1 bg-zinc-800 rounded-full"></span>
                <p class="text-[10px] font-mono text-zinc-600 uppercase">Local_Time: {new Date().toLocaleTimeString()}</p>
            </div>
            
            <div class="flex gap-8">
                <a href="/" class="text-[10px] font-black uppercase text-zinc-500 hover:text-white transition-colors tracking-widest">Privacy_Policy</a>
                <a href="/" class="text-[10px] font-black uppercase text-zinc-500 hover:text-white transition-colors tracking-widest">Terms_Of_Use</a>
            </div>
        </div>
    </div>
</footer>

<style>
    /* Menggunakan font sistem yang kuat */
    footer {
        font-family: 'Inter', sans-serif;
    }
</style>