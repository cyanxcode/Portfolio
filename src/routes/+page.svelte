<script>
	import About from "$lib/components/About.svelte";
	import Carousel from "$lib/components/Carousel.svelte";
	import ConcentricCircle from "$lib/components/ConcentricCircle.svelte";
	import CursorEffect from "$lib/components/CursorEffect.svelte";
	import FAQs from "$lib/components/FAQs.svelte";
	import Testimonial from "$lib/components/Testimonial.svelte";
	import Work from "$lib/components/Work.svelte";
  import '@fontsource/karantina';

</script>
<main  data-cursor="asteroid" class="w-full min-h-screen overflow-x-hidden cursor-default">
  
  <CursorEffect extraClass="grid place-items-center">

  <iframe
  src="https://my.spline.design/claritystream-D6CXXIB05mBhwdSjo6fw0m9z/"
  title="3D Scene"
  frameborder="0"
  width="100%"
  height="100%"
  style="border: none; "
  class="absolute top-0 left-0 w-full h-[50vw] md:h-full pointer-events-none"
  ></iframe>
    <div class="h-auto lg:h-screen box-border py-24 w-full grid place-items-center relative px-4 md:px-10">

        <div class="relative z-10 w-full flex flex-row justify-end items-center pr-5 md:px-10 lg:px-24 gap-6">
          <!-- Text Section -->
          <div class="text-right">
            <h1 class="karantina text-white text-7xl sm:text-9xl md:text-[9rem] lg:text-[10rem] xl:text-[12rem] leading-none">
              CYAN <br> STUDIOS
            </h1>
            <h2 class="text-white font-extralight text-xs md:text-md xl:text-lg">
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

<Work />
<Testimonial />


<div class="w-full h-screen overflow-hidden relative">
  <div class="w-full h-full grid grid-cols-2 absolute z-10">
    <!-- Left Column: Text -->
    <div class="flex flex-col justify-start md:justify-center items-start p-12 z-20">
      <h1 class="karantina text-white text-5xl md:text-7xl uppercase text-left leading-tight">
        <span class="text-nowrap">Bridging the gap</span> <span class="text-nowrap"> b/w design,</span><br/> code & business.
      </h1>
    </div>

    <!-- Right Column: Circle Partially Overflowing -->
    <div class="relative mb-20">
      <div class="absolute top-2/3 md:top-1/2 md:left-0 -left-40  transform -translate-y-1/2">
        <ConcentricCircle />
      </div>
    </div>
  </div>
</div>
<FAQs />
</main>