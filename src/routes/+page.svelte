<script>
	import CursorEffect from "$lib/components/CursorEffect.svelte";
    import me from "/img/me.jpg";
</script>
<main class="w-full min-h-screen bg-black">
<nav class="absolute top-10 left-10"><button class="text-white h-10 px-6 rounded-full border border-white">Menu</button></nav>
<CursorEffect extraClass=" h-screen grid place-items-center">
    <img src={me} alt="" class="absolute z-[4] w-[200px] h-[300px]">
    <img src="https://picsum.photos/200/300" alt="" class="absolute z-[3] translate-x-10 rotate-12 -mt-10 opacity-70 ">
    <h1 class="text-white text-4xl font-extralight absolute z-10 uppercase translate-y-11/12">Hello I'm <br><span class="text-8xl">Avijit Verma</span></h1>
</CursorEffect>
<div class="h-20 w-full bg-white"></div>

</main>
