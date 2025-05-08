<script>
	import About from "$lib/components/About.svelte";
	import Carousel from "$lib/components/Carousel.svelte";
	import ConcentricCircle from "$lib/components/ConcentricCircle.svelte";
	import CursorEffect from "$lib/components/CursorEffect.svelte";
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
    <div class="min-h-screen w-full grid place-items-center relative px-4 md:px-10">

        <div class="relative z-10 w-full flex flex-row justify-end items-center pr-5 md:px-10 lg:px-24 gap-6">
          
          <!-- Text Section -->
          <div class="text-right">
            <h1 class="karantina text-white text-7xl sm:text-9xl md:text-[9rem] lg:text-[10rem] xl:text-[12rem] leading-none">
              CYAN <br> STUDIOS
            </h1>
            <h2 class="text-white font-extralight text-[8px] sm:text-xs md:text-md xl:text-lg">
              A STUDIO THAT <b class="font-bold">CREATES SITES</b> FOR STARTUPS WITH <b class="font-bold">TASTE</b>
            </h2>
          </div>
      
          <!-- Image + Blur Section -->
          <div class="relative grid place-items-center shrink-0 w-40 sm:w-52 md:w-64 lg:w-72 aspect-[2/3] overflow-hidden">
            <div class="absolute z-0 w-full h-full bg-black blur-3xl"></div>
            <img src="/img/me.jpg" alt="" class="z-10 w-full h-full object-cover">
          </div>
      
        </div>
      
      </div>
</CursorEffect>
<About />
<Carousel />
    <div class="w-full h-screen">
     <div class="w-full h-screen grid grid-cols-2 absolute z-10 place-content-center">
        <div class="flex flex-col items-center">
            <h1 class=" p-20 karantina text-white text-7xl/[0.95] uppercase text-left">Bridging the gap b/w design, code & business.</h1>
            
        </div>
        <ConcentricCircle />
     </div>
    </div>
</main>