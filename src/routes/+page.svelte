<script lang="ts">
	import About from '$lib/components/About.svelte';
	import Carousel from '$lib/components/Carousel.svelte';
	import ConcentricCircle from '$lib/components/ConcentricCircle.svelte';
	import FAQs from '$lib/components/FAQs.svelte';
	import Landing from '$lib/components/Landing.svelte';
	import NewEffect from '$lib/components/NewEffect.svelte';
	import Testimonial from '$lib/components/Testimonial.svelte';
	import WhatWeOffer from '$lib/components/WhatWeOffer.svelte';
	import Work from '$lib/components/Work.svelte';
	import '@fontsource/karantina';
</script>

<svelte:head>
	<title>Cyan Studios</title>
</svelte:head>
<main data-cursor="asteroid" class="min-h-screen w-full cursor-default overflow-x-hidden">
	<Landing />
	<NewEffect />
	<Work />
	<Carousel />

	<Testimonial />
	<div class="h-32 w-full"></div>
	<About />

	<div class="relative h-screen w-full overflow-hidden">
		<div class="absolute z-10 grid h-full w-full grid-cols-2">
			<!-- Left Column: Text -->
			<div class="z-20 flex flex-col items-start justify-start p-12 md:justify-center">
				<h1 class="karantina text-left text-5xl leading-tight text-white uppercase md:text-7xl">
					<span class="text-nowrap">Bridging the gap</span>
					<span class="text-nowrap"> b/w design,</span><br /> code & business.
				</h1>
			</div>

			<!-- Right Column: Circle Partially Overflowing -->
			<div class="relative mb-20">
				<div class="absolute top-2/3 -left-40 -translate-y-1/2 transform md:top-1/2 md:left-0">
					<ConcentricCircle />
				</div>
			</div>
		</div>
	</div>
	<FAQs />
</main>
