<script>
	import WorkItems from "./WorkItems.svelte";

</script>
<h1 class="karantina text-right py-10 px-4 sm:px-8 md:px-20 text-white text-4xl sm:text-5xl md:text-7xl lg:text-8xl leading-tight uppercase">
    My Work
  </h1>
  
  <div class="grid grid-cols-1 md:grid-cols-3 px-4 sm:px-8 md:px-20 gap-4">
    <WorkItems type="tall" img="/work/Apple2.png" title="Apple Website Recreated" description="Redesigned Apple Website showcasing iPhone 15 Pro"/>    
    <WorkItems type="square" img="/work/Apple.png" title="Apple Website Recreated" description="Redesigned Apple Website showcasing iPhone 15 Pro"/>
    <WorkItems type="square" img="/work/Cybercup.png" title="Cybercup" description="Designed the Website for National Level Hackathon"/>
    <WorkItems type="wide" img="/work/Amprio.png" title="Amprio" description="A full-fledged ecommerce store for a lighting brand"/>


  
  </div>
<button class="my-10 hover:scale-105 flex items-center justify-center gap-3 px-2 py-2 rounded-full font-bold bg-white  ml-[50%] -translate-x-1/2 transition-all duration-300 ease-in-out">
    <p class="ml-4 mr-2">Show all</p>
    <img src="/extra/arrow-black-r.svg" class="w-8 hidden" alt="">
    <div class="bg-black rounded-full w-10 h-10 grid place-content-center">
        <img src="/extra/arrow-right.svg" class="w-8" alt="">
    </div>

</button>
