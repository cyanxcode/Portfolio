<script lang="ts">
	import Cursor from '$lib/components/Cursor.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import Navbar from '$lib/components/Navbar.svelte';
	import Stars from '$lib/components/Stars.svelte';
	import '../app.css';

	let { children } = $props();
</script>

<Navbar />

<Stars />
<Cursor />
{@render children()}

<Footer />