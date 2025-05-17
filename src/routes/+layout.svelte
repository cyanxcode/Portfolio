<script lang="ts">
	import Cursor from '$lib/components/Cursor.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import Navbar from '$lib/components/Navbar.svelte';
	import Stars from '$lib/components/Stars.svelte';
	import '../app.css';


	import { afterNavigate, beforeNavigate } from '$app/navigation';
  	import { onMount } from 'svelte';
  	import { tick } from 'svelte';

  	let showShutter = $state(false);
	let showSite = $state(true);

  	onMount(() => {
    	beforeNavigate(() => {
      	showShutter = true;
    });

    afterNavigate(async () => {
      	await tick();
      	setTimeout(() => (showShutter = false), 1400); // matches animation duration

		});
  	});

	let { children } = $props();
</script>

{#if showSite}
<Navbar />

<Stars />
<Cursor />
{@render children()}
<Footer />
{/if}


{#if showShutter}
	<div class="inset-0 fixed z-50">
	<div class="fixed w-full bottom-0 h-1/2 z-40 bg-black shutter pointer-events-none">
		<div class="h3 karantina uppercase fixed bottom-full left-1/2 z-50 translate-y-full  -translate-x-1/2 text-9xl text-white">Studios</div>
	</div>
	<div class="fixed w-full h-1/2 z-40 bg-black shutter-reverse pointer-events-none">
		<div class="h3 karantina uppercase fixed top-full left-1/2 z-50 -translate-y-full -translate-x-1/2  text-9xl text-white ">Cyan</div>	
	</div>
	
	</div>
{/if}
