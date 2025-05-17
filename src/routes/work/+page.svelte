<script>
	import WorkItems from "$lib/components//WorkItems.svelte";

</script>
<div class="" data-cursor="asteroid">
  <div class="w-full flex items-center justify-between mt-8 py-10 px-4 sm:px-8 md:px-20">
    <a href="/">
      <img src="/extra/left-w.svg" class="w-12 hover:scale-120 transition-all duration-200 ease-in-out" alt="">
    </a>
    <h1 class="karantina relative text-right  text-white text-4xl sm:text-5xl md:text-7xl lg:text-8xl leading-tight uppercase">
      <img src="/icons/helmet.svg" alt="" class="w-16 md:24 lg:w-32 absolute z-30 top-0 -left-2 sm:top-1 sm:left-1 md:top-3 md:left-14 lg:-top-6 -rotate-12 lg:left-7">
        My Work
    </h1></div>
  
  <div class="grid grid-cols-1  md:grid-cols-3 px-4 sm:px-8 md:px-20 gap-4 mb-40">
    <WorkItems type="tall" img="/work/Apple5.png" title="Apple Website Recreated" description="Showcasing iPhone 15 Pro"/>    
    <WorkItems type="wide" img="/work/Amprio.png" title="Amprio" description="A full-fledged ecommerce store for a lighting brand"/>
    <WorkItems type="square" img="/work/Apple.png" title="Apple Website Recreated" description="Redesigned Apple Website showcasing iPhone 15 Pro"/>
    <WorkItems type="square" img="/work/Cybercup.png" title="Cybercup" description="Designed the Website for National Level Hackathon"/>


  
  </div>
</div>  