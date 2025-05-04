<script lang="ts">
	import { fade } from "svelte/transition";

    let {children, extraClass=""} : {children?: any, extraClass: String} = $props();

    let trail: any = $state([]);
    let images = ["https://picsum.photos/300/300", "https://picsum.photos/400/300", "https://picsum.photos/100/100", "https://picsum.photos/200/100", "https://picsum.photos/300/100", "https://picsum.photos/400/100"];
    let imageIndex = 0;
    let lastTime = 0; // ⬅ Track last time image was added
    const delay = 80; // ⬅ Minimum time between image spawns (ms)


    function handleMouseMove(e: any) {const now = Date.now();
        
        if (now - lastTime > delay) {
            lastTime = now;

            const { clientX: x, clientY: y } = e;
            const id = now + Math.random();

            trail = [...trail, { id, x, y, img: images[imageIndex] }];
            imageIndex = (imageIndex + 1) % images.length;

            // Remove image after 600ms
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
