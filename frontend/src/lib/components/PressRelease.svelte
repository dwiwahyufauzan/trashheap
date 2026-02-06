<script lang="ts">
	import { fade } from 'svelte/transition';

	// --- DATA ---
	const pressItems = [
		{
			id: 1,
			date: 'FEB 01, 2024',
			category: 'STRATEGIC PARTNERSHIP',
			title: 'SBG Collective joins forces with Global Arts Alliance.',
			excerpt: 'A defining moment for Subang\'s creative economy. This partnership unlocks international funding for 12 major mural installations.',
			image: 'https://i.pinimg.com/1200x/9c/2c/f2/9c2cf29bd92a03c094aad7b9cfab2df3.jpg',
			isHero: true
		},
		{
			id: 2,
			date: 'JAN 28, 2024',
			category: 'EVENT REPORT',
			title: 'Underground Sound: The Recap.',
			excerpt: 'Over 5,000 attendees defied the rain for the biggest noise festival yet.',
			image: 'https://i.pinimg.com/1200x/50/c6/99/50c69979442b1c9da1c81f0330eff674.jpg',
			isHero: false
		},
		{
			id: 3,
			date: 'JAN 25, 2024',
			category: 'COMMUNITY',
			title: 'New Skate Park: SS15 Concrete Waves.',
			excerpt: 'Open for shredding. Designed by pro skaters for the local scene.',
			image: 'https://i.pinimg.com/1200x/ab/fc/cd/abfccddb071bc9deb8fcb8fab87e3f8b.jpg',
			isHero: false
		},
		{
			id: 4,
			date: 'JAN 20, 2024',
			category: 'PRESS COVERAGE',
			title: 'Vice Media spotlights Subang.',
			excerpt: 'The documentary "Concrete Jungle" premieres next week.',
			image: 'https://i.pinimg.com/736x/05/34/6f/05346f0334a5f34a7fbc0470a697952e.jpg',
			isHero: false
		},
        {
			id: 5,
			date: 'JAN 20, 2024',
			category: 'PRESS COVERAGE',
			title: 'Vice Media spotlights Subang.',
			excerpt: 'The documentary "Concrete Jungle" premieres next week.',
			image: 'https://images.unsplash.com/photo-1598899134739-24c46f58b8c0?q=80&w=1000&auto=format&fit=crop',
			isHero: false
		},
        {
			id: 6,
			date: 'JAN 20, 2024',
			category: 'PRESS COVERAGE',
			title: 'Vice Media spotlights Subang.',
			excerpt: 'The documentary "Concrete Jungle" premieres next week.',
			image: 'https://images.unsplash.com/photo-1598899134739-24c46f58b8c0?q=80&w=1000&auto=format&fit=crop',
			isHero: false
		}
	];

	// --- SVELTE 5 STATE ---
	let hoveredId = $state<number | null>(null);

</script>

<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous">
	<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400&family=JetBrains+Mono:wght@400;500&family=Syne:wght@400;700;800&display=swap" rel="stylesheet">
</svelte:head>

<section class="relative min-h-screen bg-white text-[#050505] overflow-hidden selection:bg-[#ccff00] selection:text-black">
	
	<div class="fixed inset-0 opacity-[0.04] pointer-events-none z-0 mix-blend-overlay" style="background-image: url('https://grainy-gradients.vercel.app/noise.svg');"></div>

	<div class="relative z-10 border-b border-white/10 bg-[#050505] py-2 overflow-hidden flex whitespace-nowrap">
		<div class="animate-marquee flex gap-8 items-center font-mono text-[10px] uppercase tracking-widest text-orange-600">
			{#each Array(10) as _}
				<span>+++ OFFICIAL PRESS RELEASE +++</span>
				<span class="text-white">SBG COLLECTIVE</span>
				<span>+++ UPDATES LIVE +++</span>
				<span class="text-white">READ NOW</span>
			{/each}
		</div>
	</div>

	<div class="max-w-[1600px] mx-auto px-4 md:px-8 py-12 md:py-20 relative z-10">
		
		<header class="flex flex-col md:flex-row md:items-end justify-between gap-8 mb-16 md:mb-24">
			<div class="max-w-4xl">
				<h1 class="text-6xl md:text-9xl font-['syne'] font-extrabold uppercase leading-[0.8] tracking-tighter text-transparent bg-clip-text bg-orange-600">
					Latest <br/> <span class="text-orange-600">News.</span>
				</h1>
			</div>

			<div class="flex flex-col items-start md:items-end gap-6">
				<p class="font-['Cormorant_Garamond'] text-xl md:text-2xl italic text-gray-700 max-w-sm text-right leading-tight">
					Curated stories from the underground. Defining the culture of tomorrow, today.
				</p>
				<button class="px-8 py-3 rounded-full text-white border bg-gray-900 border-white/20 hover:bg-orange-600 hover:text-black hover:border-orange-600 transition-all duration-300">
					<span class="font-mono text-xs uppercase tracking-widest font-bold">Download Media Kit</span>
				</button>
			</div>
		</header>

		<div 
			class="grid grid-cols-1 md:grid-cols-12 gap-4 md:gap-6 auto-rows-[minmax(300px,auto)]"
			onmouseleave={() => hoveredId = null}
			role="list"
		>
			
			{#each pressItems as item, i}
				<div class={`
					group relative rounded-3xl overflow-hidden border border-white/10 bg-zinc-900
					${item.isHero ? 'md:col-span-8 md:row-span-2 min-h-[500px] md:min-h-[700px]' : 'md:col-span-4 min-h-[400px]'}
					transition-all duration-700 ease-out
					${hoveredId !== null && hoveredId !== item.id ? 'opacity-30 scale-[0.98] blur-[2px]' : 'opacity-100 scale-100'}
				`}
				onmouseenter={() => hoveredId = item.id}
				role="listitem"
				>
					
					<div class="absolute inset-0 w-full h-full overflow-hidden">
						<img 
							src={item.image} 
							alt={item.title}
							class="w-full h-full object-cover transition-transform duration-[1.5s] ease-[cubic-bezier(0.25,1,0.5,1)] group-hover:scale-110 brightness-75 group-hover:brightness-90"
						/>
						<div class="absolute inset-0 bg-black/30 group-hover:bg-black/20 transition-all duration-500"></div>
						<div class="absolute inset-0 bg-gradient-to-t from-black via-black/50 to-transparent transition-opacity duration-500"></div>
					</div>

					<div class="absolute inset-0 p-6 md:p-10 flex flex-col justify-between">
						
						<div class="flex justify-between items-start">
							<span class="px-3 py-1 bg-black/50 backdrop-blur-md border border-white/10 rounded-full font-mono text-[10px] uppercase tracking-wider text-white">
								{item.category}
							</span>
							
						<div class="w-10 h-10 rounded-full bg-white text-black flex items-center justify-center translate-x-0 translate-y-0 opacity-100 md:translate-x-10 md:-translate-y-10 md:opacity-0 md:group-hover:translate-x-0 md:group-hover:translate-y-0 md:group-hover:opacity-100 transition-all duration-500 ease-out">
								<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="size-5 -rotate-45">
								  <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5 21 12m0 0-7.5 7.5M21 12H3" />
								</svg>
							</div>
						</div>

						<div class="transform translate-y-4 group-hover:translate-y-0 transition-transform duration-500">
							<span class="block font-mono text-orange-600 text-xs mb-3 tracking-widest">{item.date}</span>
							
							<h2 class={`
								font-['Syne'] font-bold leading-[0.9] text-white mb-4
								${item.isHero ? 'text-4xl md:text-7xl max-w-2xl' : 'text-2xl md:text-4xl'}
							`}>
								{item.title}
							</h2>

						<div class="overflow-hidden max-h-40 md:max-h-0 md:group-hover:max-h-40 transition-all duration-700 ease-in-out">
								<p class={`
									font-['Cormorant_Garamond'] text-zinc-300 italic leading-snug
									${item.isHero ? 'text-2xl max-w-xl' : 'text-lg'}
								`}>
									{item.excerpt}
								</p>
							</div>
						</div>
					</div>
				</div>
			{/each}

		</div>
	</div>
</section>

<style>
	/* Animasi untuk Marquee (Text Running) */
	@keyframes marquee {
		0% { transform: translateX(0); }
		100% { transform: translateX(-50%); }
	}
	.animate-marquee {
		animation: marquee 20s linear infinite;
	}
</style>