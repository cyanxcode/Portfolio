<script lang="ts">
	import { goto } from '$app/navigation';
	import WorkItems from './WorkItems.svelte';
	import { onMount } from 'svelte';
	import gsap from 'gsap';
	import { ScrollTrigger } from 'gsap/all';

	let textEl: any;
	let text = 'MY WORK';
	let splitText = text.split('');

	function handleClick() {
		goto('/work');
	}
	onMount(() => {
		gsap.registerPlugin(ScrollTrigger);
		let chars = textEl.querySelectorAll('.char');

		gsap.from(chars, {
			scrollTrigger: {
				trigger: textEl,
				start: 'top 80%'
			},
			y: 30,
			opacity: 0,
			stagger: 0.05,
			ease: 'power2.out'
		});
	});
</script>

<div class="" data-cursor="asteroid">
	<div class="mt-8 flex w-full justify-end">
		<h1
			bind:this={textEl}
			class="karantina relative px-6 py-10 text-right text-4xl leading-tight text-white uppercase sm:px-8 sm:text-5xl md:px-20 md:text-7xl lg:text-8xl"
		>
			<img
				src="/icons/helmet.svg"
				alt=""
				class="md:24 absolute top-0 -left-2 z-30 w-16 -rotate-12 sm:top-1 sm:left-1 md:top-3 md:left-14 lg:-top-6 lg:left-7 lg:w-32"
			/>
			{#each splitText as char, i}
				<span class="char">{char == ' ' ? '\u00A0' : char}</span>
			{/each}
		</h1>
	</div>

	<div class="grid grid-cols-1 gap-4 px-6 md:grid-cols-3 md:px-24">
		<WorkItems
			type="tall"
			img="/work/Apple3.png"
			title="Apple Website Recreated"
			description="Showcasing iPhone 15 Pro"
		/>
		<WorkItems
			type="wide"
			img="/work/Amprio.png"
			title="Amprio"
			description="A full-fledged ecommerce store for a lighting brand"
		/>
		<WorkItems
			type="square"
			img="/work/Mor.png"
			title="Mor Confezzione"
			description="A website for a clothing brand"
		/>
		<WorkItems
			type="square"
			img="/work/Cybercup.png"
			title="Cybercup"
			description="Designed the Website for National Level Hackathon"
		/>
	</div>
	<button
		data-cursor="click"
		onclick={handleClick}
		class="my-10 ml-[50%] flex -translate-x-1/2 items-center justify-center gap-3 rounded-full bg-white px-2 py-2 font-bold transition-all duration-300 ease-in-out hover:scale-105"
	>
		<p class="mr-2 ml-4">Show all</p>
		<img src="/extra/arrow-black-r.svg" class="hidden w-8" alt="" />
		<div class="grid h-10 w-10 place-content-center rounded-full bg-black">
			<img src="/extra/arrow-right.svg" class="w-8" alt="" />
		</div>
	</button>
</div>
