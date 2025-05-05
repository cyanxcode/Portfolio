<script>
	import ConcentricCircle from "$lib/components/ConcentricCircle.svelte";
	import CursorEffect from "$lib/components/CursorEffect.svelte";
    import me from "$lib/img/me.jpg";
    import '@fontsource/karantina';
</script>
<main class="w-full min-h-screen bg-black overflow-x-hidden">

    <nav class="w-full h-24 absolute text-white flex justify-start items-center text-md uppercase gap-10 px-10 font-mono">
        <a href="#about">ABOUT</a>
        <a href="#about">WORK</a>
        <a href="#about">FAQs</a>
        <a href="#about">CONTACT</a>
    </nav>
<CursorEffect extraClass="min-h-screen grid place-items-center">
    <div class=" h-screen w-full grid place-items-center">

    <div class="absolute z-10 w-full mr-32 flex justify-end items-center">
        <h1 class="karantina text-white text-[9rem]/[0.95] text-right">CYAN <br> STUDIOS</h1>
        <div class="grid place-items-center relative w-84">
            <div class="flex p-10 bg-black blur-3xl w-96 h-96 absolute z-20">
            </div>
                <img src={me} alt="" class="z-30 absolute w-60 h-84">
            </div>
     </div>
    </div>
    <div class="w-full h-screen">
     <div class="w-full h-screen grid grid-cols-2 absolute z-10 place-content-center">
        <h1 class=" p-20 karantina text-white text-7xl/[0.95] uppercase text-left">Bridging the gap b/w design, code & business.</h1>
        <ConcentricCircle />
     </div>
    </div>
     
</CursorEffect>
</main>
<style>
    .karantina {
        font-family: 'Karantina';
        src: url('/fonts/Karantina-Regular.ttf') format('truetype');
        font-weight: normal;
        font-style: normal;
    }
</style>