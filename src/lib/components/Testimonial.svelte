<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';
	import { ScrollTrigger } from 'gsap/all';

	let textEl: any;
	let text = 'Testimonial';
	let splitText = text.split('');
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
	const testimonials = [
		{
			name: 'Dr. Shilpi Sharma',
			title: 'Dept HOD',
			company: 'Amity University',
			img: '/img/testimonial1.jpeg',
			quote:
				'I am confident that Avijit Verma has the intellectual capabilities, motivation and determination required to succeed in his future endeavors. I am certain that he will contribute positively to any organization.'
		},
		{
			name: 'Harry Klair',
			title: '',
			company: 'Mor Confezzione',
			img: '/img/default.jpg',
			quote:
				'Working with Avijit was incredible. I had an idea and no clue how to bring it to life, and he delivered a professional website that impresssed our potential clients from day one.'
		}
	];

	/*

	 {
			name: 'Rudrakshi Aggarwal',
			title: 'Co Founder',
			company: 'Amprio',
			img: '/img/testimonial2.jpeg',
			quote:
				'Good work and great communication skills, can fit in any environment and have exceptional technical knowledge.'
		}
	 */
</script>

<div class="flex items-end gap-4 py-10">
	<h1
		bind:this={textEl}
		class="karantina pl-4 text-left text-4xl leading-tight text-white uppercase sm:pl-8 sm:text-5xl md:pl-20 md:text-7xl lg:text-8xl"
	>
		{#each splitText as char}
			<span class="char">{char == ' ' ? '\u00A0' : char}</span>
		{/each}
	</h1>
	<img src="/icons/bb8.svg" alt="" class=" -ml-5 w-20 md:w-40" />
</div>
<div class="flex w-full flex-col items-center space-y-6 px-4 sm:px-8 md:px-20">
	{#each testimonials as testimonial}
		<div
			class="group flex w-full flex-col gap-4 rounded-xl bg-white p-4 text-black transition-colors duration-300 sm:p-6 md:flex-row md:items-center md:bg-black md:text-white md:hover:bg-white md:hover:text-black"
		>
			<!-- Profile Section -->
			<div class="flex w-full items-center gap-4 md:w-[40%]">
				<div
					class="h-14 w-14 shrink-0 overflow-hidden rounded-full bg-black sm:h-16 sm:w-16 md:bg-white md:group-hover:bg-black"
				>
					<img
						src={testimonial.img}
						alt={testimonial.name}
						class="h-full w-full rounded-full object-cover"
					/>
				</div>
				<div class="flex flex-col">
					<p class="text-lg leading-tight font-medium sm:text-xl">{testimonial.name}</p>
					{#if testimonial.title}
						<p
							class="text-sm text-zinc-600 sm:text-base md:text-zinc-300 md:group-hover:text-zinc-600"
						>
							{testimonial.title}
						</p>
					{/if}
					{#if testimonial.company}
						<p
							class="text-sm text-zinc-600 sm:text-base md:text-zinc-300 md:group-hover:text-zinc-600"
						>
							{testimonial.company}
						</p>
					{/if}
				</div>
			</div>

			<!-- Quote -->
			<p class="w-full text-base font-semibold italic sm:text-lg md:w-[60%] md:text-xl">
				“{testimonial.quote}”
			</p>
		</div>

		<!-- Divider -->
		{#if !(testimonials[testimonials.length - 1] === testimonial)}
			<div class="h-[1px] w-full bg-zinc-300"></div>
		{/if}
	{/each}
</div>
