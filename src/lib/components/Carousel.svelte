<script>
	import { onMount } from 'svelte';

	onMount(() => {
		if (!document.querySelector('script[src*="embed.js"]')) {
			const script = document.createElement('script');
			script.src = 'https://asset-tidycal.b-cdn.net/js/embed.js';
			script.async = true;
			document.body.appendChild(script);
		}
	});

	function openTidyCalPopup() {
		// This assumes TidyCal exposes a global method (like Calendly does). If not, this won't work.
		// TidyCal unfortunately does not provide an official popup API as of now.
		window.open('https://tidycal.com/codinginstant/15-minute-meeting', '_blank');
	}
</script>

<div class="hide-scrollbar overflow-x-auto" data-cursor="asteroid">
	<div
		class="flex w-full snap-x snap-mandatory flex-row gap-5 px-4 py-8 xl:mr-2 xl:grid xl:grid-cols-4"
		style="scroll-behavior: smooth;"
	>
		<div
			class=" hover:sclae-105 relative h-96 w-84 flex-shrink-0 snap-start overflow-hidden rounded-2xl transition-all duration-300 ease-initial hover:scale-[1.02] xl:w-full"
		>
			<img src="/cards/card-5.svg" class="h-full w-full object-cover" alt="" />
			<div
				class="absolute top-0 left-0 z-10 flex h-full w-full flex-col items-center justify-center gap-4 p-4"
			>
				<h4 class="text-center text-4xl text-white">Let’s Talk About <br /> Your Project</h4>
				<p class="text-center font-extralight text-white">
					Schedule a free 15-minute call to <br />discuss your ideas.
				</p>
				<button
					onclick={openTidyCalPopup}
					data-cursor="click"
					class="my-4 h-12 w-[80%] rounded-lg bg-white">Book a call</button
				>
				<div class="flex w-full justify-between px-4">
					<div class="text-white">
						<a href="mailto:avijitv1205@gmail.com" class="font-medium">Prefer to email?</a>
						<a href="mailto:avijitv1205@gmail.com" class="text-sm font-light text-zinc-300"
							>avijitv1205@gmail.com</a
						>
					</div>
					<a
						href="mailto:avijitv1205@gmail.com"
						data-cursor="click"
						class="flex aspect-square h-12 w-12 items-center justify-center rounded-full bg-white"
					>
						<img src="/extra/arrow-black-r.svg" class="w-7" alt="" />
					</a>
				</div>
			</div>
		</div>

		<div
			class="  hover:sclae-105 relative h-96 w-84 flex-shrink-0 snap-start overflow-hidden rounded-2xl transition-all duration-300 ease-initial hover:scale-[1.02] xl:w-full"
		>
			<img src="/cards/card-7.svg" class="h-full w-full object-cover" alt="" />
			<div
				class="absolute top-0 left-0 z-10 flex h-full w-full flex-col items-center justify-center gap-4 p-4"
			>
				<img src="/icons/figma.svg" alt="" class="w-16 pb-8" />
				<h4 class="font-b text-center text-4xl text-white shadow-2xl">UI / UX Design</h4>
				<p class="text-center text-lg font-light text-zinc-200">
					From wireframes to final visuals, I create smooth, modern designs your users will love.
				</p>
			</div>
		</div>
		<div
			class=" hover:sclae-105 relative h-96 w-84 flex-shrink-0 snap-start overflow-hidden rounded-2xl transition-all duration-300 ease-initial hover:scale-[1.02] xl:w-full"
		>
			<img src="/cards/card-8.svg" class="h-full w-full object-cover" alt="" />
			<div
				class="absolute top-0 left-0 z-10 flex h-full w-full flex-col items-center justify-center gap-4 p-4"
			>
				<div
					class=" absolute z-20 h-full w-full bg-gradient-to-t from-black via-transparent to-transparent"
				></div>
				<h4 class="font-b w-full text-left text-4xl text-white shadow-2xl">Design System</h4>
				<p class="text-left text-lg font-light text-zinc-200 text-shadow-md">
					I create flexible websites powered by cutting-edge tools and modern frameworks.
				</p>
				<img src="/extra/bracket.svg" alt="" class="w-16 pt-8" />
			</div>
		</div>

		<div
			class=" hover:sclae-105 relative h-96 w-84 flex-shrink-0 snap-start overflow-hidden rounded-2xl transition-all duration-300 ease-initial hover:scale-[1.02] xl:w-full"
		>
			<img src="/cards/card-4.svg" class="h-full w-full object-cover" alt="" />
			<div
				class="absolute top-0 left-0 z-10 flex h-full w-full flex-col items-center justify-center gap-4 p-4"
			>
				<img src="/extra/home.svg" alt="" class="w-16 pb-8" />
				<h4 class="font-b text-center text-4xl text-white shadow-2xl">Branding</h4>
				<p class="text-center text-lg font-normal text-zinc-200 text-shadow-md">
					I help you create a strong visual identity — from logos to colors — that makes your brand
					stand out.
				</p>
			</div>
		</div>
	</div>
</div>

<style>
	.hide-scrollbar::-webkit-scrollbar {
		display: none;
	}

	.hide-scrollbar {
		-ms-overflow-style: none;
		scrollbar-width: none;
	}
</style>
