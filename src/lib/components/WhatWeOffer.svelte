<script lang="ts">
	import Pricing from '$lib/components/Pricing.svelte'; // Update this path if needed
	import { onMount } from 'svelte';
	import gsap from 'gsap';
	import { ScrollTrigger } from 'gsap/all';

	// Define pricing data in an array for cleaner code
	const pricingTiers = [
		{
			idx: 1,
			title: 'Landing Page',
			time: 'Landing Page: 2-3 weeks',
			pricingDesc: 'starting from',
			pricing: '$800',
			desc: 'A landing page is a single web page designed to capture leads or promote a specific product or service, often with a clear call to action.'
		},
		{
			idx: 2,
			title: 'Promo Website',
			time: 'Promo Website: 3-4 weeks',
			pricingDesc: 'starting from',
			pricing: '$1200',
			desc: 'A promo website is a great way to showcase your product or service, providing essential information and a clear call to action.'
		},
		{
			idx: 3,
			title: 'Ecommerce Website',
			time: 'Ecommerce Website: 4-6 weeks',
			pricingDesc: 'starting from',
			pricing: '$2000',
			desc: 'An ecommerce website is a powerful tool for selling products online, providing a seamless shopping experience for customers.'
		},
		{
			idx: 4,
			title: 'Custom Web App',
			time: 'Custom Web App: 6-8 weeks',
			pricingDesc: '',
			pricing: 'custom',
			desc: 'A custom web app is tailored to your specific business needs, offering unique features and functionality to enhance user experience and drive engagement.'
		}
	];

	let textEl: HTMLElement;
	let text = 'What We Offer';
	let splitText = text.split('');

	onMount(() => {
		gsap.registerPlugin(ScrollTrigger);

		// Animate heading characters
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

		// Animate each pricing item on reveal
		gsap.utils.toArray('.pricing-item').forEach((item) => {
			gsap.from(item as HTMLElement, {
				scrollTrigger: {
					trigger: item as HTMLElement,
					start: 'top 85%', // Start animation when 85% of the viewport is hit
					toggleActions: 'play none none none' // Play animation once and don't reverse
				},
				opacity: 0,
				y: 60, // Slide up from 60px below
				duration: 1,
				ease: 'power3.out'
			});
		});
	});
</script>

<div class="mt-32 flex items-end gap-4 py-10">
	<h1
		bind:this={textEl}
		class="karantina pl-4 text-left text-4xl leading-tight text-white uppercase sm:pl-8 sm:text-5xl md:pl-20 md:text-7xl lg:text-8xl"
	>
		{#each splitText as char}
			<span class="char">{char === ' ' ? '\u00A0' : char}</span>
		{/each}
	</h1>
</div>

<div class="flex flex-col">
	{#each pricingTiers as tier (tier.idx)}
		<Pricing
			class="pricing-item"
			idx={tier.idx}
			title={tier.title}
			time={tier.time}
			pricingDesc={tier.pricingDesc}
			pricing={tier.pricing}
			desc={tier.desc}
		/>
	{/each}
</div>
