<script lang="ts">

	import { afterNavigate, beforeNavigate } from '$app/navigation';
  	import { onMount } from 'svelte';
  	import { tick } from 'svelte';
    import { goto } from '$app/navigation';


  	let showShutter = $state(false);
    let toGo = $state("Cyan");
    let isNavigating = false;

    onMount(() => {
        beforeNavigate((nav) => {
            if (isNavigating || !nav.to?.url) {
                return
            }
            toGo = (nav.to?.url.pathname.split('/').at(-1)?? 'Cyan Studios').replaceAll("%20", ' ').toUpperCase();
            nav.cancel(); // cancel default navigation
            isNavigating = true;

            showShutter = true;

            // wait for animation to finish, then gos
			setTimeout(() => {
				const target = nav.to!.url;
				goto(`${target.pathname}${target.search}${target.hash}`);
			}, 200);

        });
    });

    afterNavigate(async () => {
		isNavigating = false;
      	await tick();
      	setTimeout(() => (showShutter = false), 800); // matches animation duration
		});

</script>


<div class="">
{#if showShutter}
	<div class="inset-0 fixed z-50">
	    <div class="fixed w-full bottom-0 h-1/2 z-40 bg-black shutter pointer-events-none">
	    	<div class="h3 karantina uppercase fixed bottom-full left-1/2 z-50 translate-y-full  -translate-x-1/2 text-9xl text-white"></div>
	    </div>
	    <div class="fixed w-full h-[calc(50%+2px)] z-40 bg-black shutter-reverse pointer-events-none">
	    	<div class="h3 karantina uppercase fixed top-full left-1/2 z-50 -translate-x-1/2 -translate-y-1/2 whitespace-nowrap text-6xl md:text-7xl lg:text-9xl text-white ">
                {#if toGo}
                    {toGo}
                {:else}
                    CYAN STUDIOS
                {/if}
            </div>	
	    </div>
	</div>
{/if}
</div>