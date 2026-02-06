<script lang="ts">
	/* Svelte 5 Rune State (Optional, but good practice) */
	let newsItems = [
		{
			date: '14:00',
			label: 'FEATURED TODAY',
			title: 'New collaborative mural project announced with Arts Council.',
			// Gambar Landscape Besar untuk Headline
			image: 'https://i.pinimg.com/1200x/a5/5a/82/a55a8279fcfc66193ecbcce8bbf5feba.jpg', 
			excerpt: 'A groundbreaking initiative transforming the city gray walls into canvases of expression.'
		},
		{
			date: 'RECAP',
			label: 'YESTERDAY',
			title: 'The punk scene is alive in Subang.',
			image: 'https://i.pinimg.com/1200x/f3/f6/f4/f3f6f473ea782785e9680b62a821b1f9.jpg',
			excerpt: 'Underground gigs are surfacing again.'
		},
		{
			date: 'GUIDE',
			label: '2 DAYS AGO',
			title: 'Vinyl hunting: Best spots in district.',
			image: 'https://i.pinimg.com/736x/2d/38/ca/2d38caa1d6e06721c3f02aa8d6e4e25b.jpg',
			excerpt: 'Where to find the rarest gems.'
		}
	];
</script>

<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous">
	<link href="https://fonts.googleapis.com/css2?family=EB+Garamond:ital,wght@0,400;0,600;1,400&family=Syne:wght@400;700;800&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
</svelte:head>

<main class="relative min-h-screen w-full bg-[#080808] text-white p-4 md:p-8 font-sans selection:bg-orange-600 selection:text-black">
	
	<div class="fixed inset-0 opacity-[0.03] pointer-events-none z-0 mix-blend-overlay" 
		 style="background-image: url('https://grainy-gradients.vercel.app/noise.svg');">
	</div>

	<div class="relative z-10 max-w-7xl mx-auto">
		
		<header class="flex flex-col md:flex-row md:items-end justify-between mb-12 md:mb-20 border-b border-white/10 pb-6">
			<div>
				<span class="block font-mono text-xs text-orange-600 mb-2 tracking-widest">● LIVE FEED</span>
				<h1 class="text-7xl md:text-9xl font-['Syne'] font-extrabold uppercase leading-[0.85] tracking-tighter">
					The <span class="font-['EB_Garamond'] font-normal italic lowercase text-white/60">Zine</span>.
				</h1>
			</div>
			<div class="mt-8 md:mt-0 text-right">
				<div class="inline-flex flex-col items-end">
					<span class="text-xs font-mono text-gray-500 uppercase tracking-widest">Volume 001</span>
					<span class="text-xs font-mono text-gray-500 uppercase tracking-widest">Subang Underground</span>
				</div>
			</div>
		</header>

		<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-12 gap-6">
			
			<div class="col-span-1 md:col-span-12">
				{@render card(newsItems[0], true)}
			</div>

			{#each newsItems.slice(1) as item, i}
				<div class="col-span-1 md:col-span-6">
					{@render card(item, false)}
				</div>
			{/each}
			
		</div>

		<div class="mt-20 flex justify-center pb-12">
			<button class="group relative px-10 py-4 bg-white text-black rounded-full overflow-hidden transition-all hover:scale-105">
				<div class="absolute inset-0 bg-orange-600 translate-y-full group-hover:translate-y-0 transition-transform duration-300 ease-out"></div>
				<span class="relative z-10 font-['Syne'] font-bold text-sm uppercase tracking-widest group-hover:tracking-[0.3em] transition-all">
					View All Archives
				</span>
			</button>
		</div>

	</div>
</main>

{#snippet card(item: any, isHero: boolean)}
	<article class="group relative block w-full h-full cursor-pointer">
		
		<div class={`relative overflow-hidden rounded-[2rem] bg-gray-900 border border-white/10 ${isHero ? 'aspect-[4/5] md:aspect-[21/9]' : 'aspect-[4/5] md:aspect-[4/3]'}`}>
			
			<img 
				src={item.image} 
				alt={item.title}
				class="w-full h-full object-cover transition-transform duration-1000 ease-[cubic-bezier(0.25,1,0.5,1)] group-hover:scale-105 brightness-75 group-hover:brightness-90"
			/>
			
			<div class="absolute inset-0 bg-black/30 group-hover:bg-black/20 transition-all duration-500"></div>
			<div class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/30 to-transparent transition-opacity duration-500"></div>

			<div class="absolute top-6 left-6 md:top-8 md:left-8 flex items-center gap-3">
				<div class="backdrop-blur-md bg-white border border-white/20 px-3 py-3 rounded-full">
					<span class="text-[10px] font-bold text-white uppercase tracking-widest font-['Syne']">
						{item.category}
					</span>
				</div>
			</div>

			<div class="absolute top-6 right-6 md:top-8 md:right-8 w-12 h-12 rounded-full bg-white text-gray-900 backdrop-blur-md flex items-center justify-center border border-white/20 opacity-100 translate-y-0 md:opacity-0 md:-translate-y-4 md:group-hover:translate-y-0 md:group-hover:opacity-100 transition-all duration-500">
				<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-5 -rotate-45">
				  <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5 21 12m0 0-7.5 7.5M21 12H3" />
				</svg>
			</div>

			<div class="absolute bottom-0 left-0 w-full p-6 md:p-10 transform translate-y-2 group-hover:translate-y-0 transition-transform duration-500">
				
				<div class="flex items-center gap-4 mb-3 text-white/60 font-mono text-xs overflow-hidden">
					<span>{item.label}</span>
					<span class="w-px h-3 bg-white"></span>
					<span>{item.date}</span>
				</div>

				<h2 class={`${isHero ? 'text-3xl md:text-6xl' : 'text-2xl md:text-4xl'} font-['Syne'] font-bold leading-[0.9] text-white mb-2 group-hover:text-white transition-colors duration-300`}>
					{item.title}
				</h2>

				<p class="font-['EB_Garamond'] italic text-lg md:text-xl text-white/70 max-w-xl opacity-100 translate-y-0 md:opacity-0 md:translate-y-4 md:group-hover:opacity-100 md:group-hover:translate-y-0 transition-all duration-500 delay-75">
					{item.excerpt || 'Read the full story...'}
				</p>
			</div>

		</div>
	</article>
{/snippet}

<style>
	/* Memastikan font rendering tajam */
	:global(body) {
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}
</style>