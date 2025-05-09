<script lang="ts">
	import Navbar from '$lib/components/Navbar.svelte';
	import Stars from '$lib/components/Stars.svelte';
	import '../app.css';

	let { children } = $props();
</script>

<Navbar />
<Stars />
{@render children()}
