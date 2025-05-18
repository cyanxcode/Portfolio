<script lang=ts>
	import About from "$lib/components/About.svelte";
	import Carousel from "$lib/components/Carousel.svelte";
	import ConcentricCircle from "$lib/components/ConcentricCircle.svelte";
	import FAQs from "$lib/components/FAQs.svelte";
	import Landing from "$lib/components/Landing.svelte";
	import Testimonial from "$lib/components/Testimonial.svelte";
	import Work from "$lib/components/Work.svelte";
  import '@fontsource/karantina';

</script>

<svelte:head>
	<title>Cyan Studios</title>
</svelte:head>
<main  data-cursor="asteroid" class="w-full min-h-screen overflow-x-hidden cursor-default">
  <Landing />
  
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
