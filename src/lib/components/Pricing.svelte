<script lang="ts">
	// Use Svelte 5 runes for props
	let { idx, title, time, pricingDesc, pricing, desc, class: className = '' } = $props();
</script>

<div class="{className} flex flex-col items-center text-white">
	<div class="w-full px-8 py-4 text-left text-4xl font-bold md:px-12">{idx}</div>
	<div class="h-[1px] w-[calc(100%-64px)] bg-white md:w-[calc(100%-80px)]"></div>

	<div class="grid w-full gap-6 p-8 md:p-10 lg:grid-cols-3 lg:gap-4">
		<div class="cols-span-1 flex flex-col items-start justify-center gap-4 lg:ml-10">
			<h3 class="text-3xl font-semibold">{title}</h3>
			<div>
				<p class="font-medium">Est Delivery Time</p>
				<p class="font-light text-zinc-300">{time}</p>
			</div>
			<div>
				<p class="font-light text-zinc-300">40% deposit before commencement</p>
				<p class="font-light text-zinc-300">1 round of revision</p>
			</div>
			<p class="text-lg">
				{pricingDesc} <span class="text-3xl font-bold">{pricing}</span> USD
			</p>
		</div>

		<div class="col-span-2 flex w-full items-center">
			<p class="text-lg leading-relaxed text-zinc-200">
				{desc}
			</p>
		</div>
	</div>
</div>
