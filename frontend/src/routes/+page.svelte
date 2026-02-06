<script lang="ts">
	import Hero from '$lib/components/Hero.svelte';
	import TickerTape from '$lib/components/TickerTape.svelte';
	import Activities from '$lib/components/Activities.svelte';
	import News from '$lib/components/News.svelte';
	import Newsletter from '$lib/components/Newsletter.svelte';
	import PressRelease from '$lib/components/PressRelease.svelte';
	import Merch from '$lib/components/Merch.svelte';
</script>

<Hero />
<TickerTape />

<!-- Main Content Area -->
<div class="flex justify-center px-4 md:px-10 py-16">
	<div class="flex flex-col max-w-300 w-full gap-20">
		<Activities />
		<News />
		<PressRelease />
		<Merch />
		<Newsletter />
	</div>
</div>
