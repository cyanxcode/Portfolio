<script lang="ts">
	import { fade } from "svelte/transition";

    let {children, extraClass=""} : {children?: any, extraClass: String} = $props();

    let trail: any = $state([]);
    let images = ["/img/cursor/Apple.png", "/img/cursor/Cyan.jpg", "/img/cursor/Cybercup.png", "/img/cursor/Realm.png"];
    let imageIndex = 0;
    let lastX = 0;
let lastY = 0;
const distanceThreshold = 80;

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

		trail = [...trail, { id, x, y, img: images[imageIndex] }];
		imageIndex = (imageIndex + 1) % images.length;

		setTimeout(() => {
			trail = trail.filter((t: any) => t.id !== id);
		}, 400);
	}
}
    

</script>


<div role="presentation" class={`${extraClass}`} onmousemove={handleMouseMove}>
    {@render children?.()}
    {#each trail as t (t.id)}
      <img
        src={t.img}
        alt=""
        class="pointer-events-none -translate-x-1/2 -translate-y-1/2 w-40 h-24 object-cover absolute opacity-80 transition-opacity duration-500"
        style="top: {t.y}px; left: {t.x}px;"
        out:fade={{ duration: 300 }}
      />
    {/each}
</div>
