<script lang="ts">
	import { scale, blur } from 'svelte/transition';

	let { children, extraClass = '' }: { children?: any; extraClass: String } = $props();

	let trail: any = $state([]);
	let images = [
		'/img/cursor/Apple.png',
		'/img/cursor/Cyan.jpg',
		'/img/cursor/Cybercup.png',
		'/img/cursor/Realm.png'
	];
	let imageIndex = 0;
	let lastX = 0;
	let lastY = 0;
	const distanceThreshold = 120;

	function handleMouseMove(e: MouseEvent) {
		const { pageX: x, pageY: y } = e;

		// Calculate distance from last point
		const dx = x - lastX;
		const dy = y - lastY;
		const distance = Math.sqrt(dx * dx + dy * dy);

		if (distance > distanceThreshold) {
			lastX = x;
			lastY = y;

			const id = Date.now() + Math.random();
			trail = [...trail, { id, x, y, img: images[imageIndex], isRemoving: false }];

			imageIndex = (imageIndex + 1) % images.length;

			setTimeout(() => {
				trail = trail.map((t: any) => (t.id === id ? { ...t, isRemoving: true } : t));

				setTimeout(() => {
					trail = trail.filter((t: any) => t.id !== id);
				}, 500); // match CSS animation duration
			}, 100); // optional slight delay before applying removal
		}
	}
</script>

<div
	data-cursor="close"
	role="presentation"
	class={`${extraClass} -z-10`}
	onmousemove={handleMouseMove}
>
	{@render children?.()}
	{#each trail as t (t.id)}
		<img
			src={t.img}
			alt=""
			class={`pointer-events-none absolute h-36 w-64 shrink -translate-x-1/2 -translate-y-1/2 rounded-xl object-cover opacity-80 transition-all	 ease-out ${t.isRemoving ? 'scale-blur-out' : ''}`}
			style="top: {t.y}px; left: {t.x}px;"
		/>
	{/each}
</div>

<style>
	.scale-blur-out {
		transform: scale(0.8);
		filter: blur(8px);
		opacity: 0;
		transition:
			transform 0.5s ease-out,
			filter 1s ease-out,
			opacity 0.5s ease-out;
	}
</style>
