<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';
	import { ScrollTrigger } from 'gsap/ScrollTrigger';
	import { browser } from '$app/environment';

	let textEL: any;
	let paraEl: any;
	let text = 'ABOUT AVIJIT VERMA';
	let splitText = text.split('');

	let isScrolling = $state(false);
	let timeout: ReturnType<typeof setTimeout>;

	let marqueeEl: HTMLDivElement;
	let offset = $state(0);
	let direction = $state(1);
	let speed = 1.4;
	let lastScrollTop = $state(0);

	const handleScroll = () => {
		const currentScroll = window.scrollY;

		if (currentScroll > lastScrollTop) {
			// Scrolling down
			direction = 1;
		} else if (currentScroll < lastScrollTop) {
			// Scrolling up
			direction = -1;
		}

		lastScrollTop = currentScroll <= 0 ? 0 : currentScroll; // Prevent negative values
	};

	onMount(() => {
		if (!browser) return;
		gsap.registerPlugin(ScrollTrigger);
		const animate = () => {
			offset += direction * speed;

			// Loop back seamlessly
			const totalWidth = marqueeEl.scrollWidth / 3;

			if (direction === -1 && offset <= -totalWidth) {
				offset = 0;
			}
			if (direction === 1 && offset >= 0) {
				offset = -totalWidth;
			}

			marqueeEl.style.transform = `translateX(${offset}px)`;
			requestAnimationFrame(animate);
		};

		let chars = textEL.querySelectorAll('.char');

		gsap.from(chars, {
			scrollTrigger: {
				trigger: textEL,
				start: 'top 80%'
			},
			y: 30,
			opacity: 0,
			stagger: 0.05,
			ease: 'power2.out'
		});
		gsap.from(paraEl, {
			scrollTrigger: {
				trigger: paraEl,
				start: 'top 80%'
			},
			y: 30,
			opacity: 0,
			duration: 1
		});

		requestAnimationFrame(animate);
	});
</script>

<svelte:window on:scroll={handleScroll} />
<main class="w-full py-10" data-cursor="asteroid">
	<div class="relative grid w-full grid-cols-2 px-3 md:px-10 lg:px-16">
		<div class="flex justify-center md:justify-end">
			<img
				src="/img/profile.jpeg"
				alt="Avijit Verma"
				class="h-[22rem] w-full max-w-md rounded-lg object-cover shadow-md md:h-[26rem] lg:h-[30rem]"
			/>
		</div>
		<!-- Text Section -->
		<div class="flex flex-col items-start gap-1 p-4 text-left md:gap-6 md:p-8">
			<h1
				bind:this={textEL}
				class="karantina text-left text-5xl leading-tight whitespace-nowrap text-white uppercase md:text-7xl lg:text-8xl"
			>
				{#each splitText as char, i}
					{#if i == 5}
						<br />
					{:else}
						<span class="char">{char == ' ' ? '\u00A0' : char}</span>
					{/if}
				{/each}
			</h1>
			<p
				bind:this={paraEl}
				class="max-w-md text-sm font-extralight text-white sm:text-base md:text-lg lg:text-xl"
			>
				I am a full-stack developer who turns bold ideas into reality. I specialize in blending code
				with modern design to craft applications that don't just look great - but perform.
			</p>
		</div>

		<!-- Image -->

		<!-- Button with Arc Text -->
		<a
			href="https://rxresu.me/codinginstant/cyan"
			target="_blank"
			data-cursor="icon"
			class="absolute top-full left-1/2 z-10 aspect-square w-28 -translate-x-1/2 -translate-y-1/2 cursor-none rounded-full border-[10px] border-black bg-blue-600 font-medium text-white transition-all duration-300 ease-in-out hover:scale-105 md:w-32 md:border-[12px]"
		>
			<!-- Arc Text SVG -->
			<svg class="absolute inset-0 -mt-2 h-full w-full" viewBox="0 0 100 100">
				<defs>
					<path id="arcPath" d="M10,60 A40,40 0 0,1 90,60" />
				</defs>
				<text
					fill="white"
					font-size="10"
					font-weight="400"
					style="letter-spacing: 1px;"
					class="font-bold"
				>
					<textPath href="#arcPath" startOffset="50%" text-anchor="middle">
						GET MY RESUME
					</textPath>
				</text>
			</svg>
			<img
				src="/extra/arrow-top-r.svg"
				alt=""
				class="absolute top-1/2 left-1/2 w-8 -translate-1/2 md:w-10"
			/>
		</a>
	</div>

	<!-- ✅ Marquee Section -->
	<div class="mt-4 mb-24 h-28 overflow-hidden bg-zinc-200 md:h-36">
		<div bind:this={marqueeEl} class="animate-scroll flex h-full w-max whitespace-nowrap">
			{#each Array(3) as _}
				<div class="flex h-full items-center justify-between gap-16 px-6 text-black md:gap-32">
					<img src="/extra/star4.svg" alt="" class="w-4 md:w-6" />
					<h1 class="karantina text-center text-3xl md:text-4xl lg:text-5xl">Web Developer</h1>
					<img src="/extra/star4.svg" alt="" class="w-4 md:w-6" />
					<h1 class="karantina text-center text-3xl md:text-4xl lg:text-5xl">UI Designer</h1>
					<img src="/extra/star4.svg" alt="" class="w-4 md:w-6" />
					<h1 class="karantina text-center text-3xl md:text-4xl lg:text-5xl">Engineer</h1>
				</div>

				<div class="w-4 md:w-20"></div>
			{/each}
		</div>
	</div>
</main>
