<script>
  import { onMount } from 'svelte';

  onMount(() => {
    if (!document.querySelector('script[src*="embed.js"]')) {
      const script = document.createElement('script');
      script.src = 'https://asset-tidycal.b-cdn.net/js/embed.js';
      script.async = true;
      document.body.appendChild(script);
    }
  });

  function openTidyCalPopup() {
    // This assumes TidyCal exposes a global method (like Calendly does). If not, this won't work.
    // TidyCal unfortunately does not provide an official popup API as of now.
    window.open('https://tidycal.com/codinginstant/15-minute-meeting', '_blank');
  }
</script>


<div class="overflow-x-auto hide-scrollbar" data-cursor="asteroid">
    <div class="w-full snap-x snap-mandatory flex xl:grid xl:grid-cols-4 xl:mr-2 gap-5 flex-row px-4 py-8"
    style="scroll-behavior: smooth;"
    >

    <div class=" snap-start w-84 xl:w-full h-96 flex-shrink-0 rounded-2xl overflow-hidden relative hover:scale-[1.02] hover:-translate-y-6 transition-all duration-300 ease-initial">
      <img src="/cards/card-5.svg" class="w-full h-full object-cover" alt="">
      <div class="absolute z-10 top-0 left-0 w-full h-full flex flex-col p-4 items-center justify-center gap-4">
        <h4 class="text-white text-4xl text-center">Let’s Talk About <br/> Your Project</h4>
        <p class="text-white text-center font-extralight">Schedule a free 15-minute call to <br>discuss your ideas.</p>
        <button onclick={openTidyCalPopup} data-cursor="click" class="my-4 bg-white w-[80%] h-12 rounded-lg">Book a call</button>
        <div class="flex w-full px-4 justify-between">
          <div class="text-white">
            <a href="mailto:avijitv1205@gmail.com" class="font-medium">Prefer to email?</a>
            <a href="mailto:avijitv1205@gmail.com" class="font-light text-sm text-zinc-300">avijitv1205@gmail.com</a>
          </div>
          <a href="mailto:avijitv1205@gmail.com" data-cursor="click" class="aspect-square w-12 h-12 bg-white rounded-full flex items-center justify-center ">
            <img src="/extra/arrow-black-r.svg" class="w-7" alt="">
          </a>
        </div>
      </div>
    </div>
        
        <div class="  snap-start w-84 xl:w-full h-96 flex-shrink-0 rounded-2xl overflow-hidden relative hover:scale-[1.02] hover:-translate-y-6 transition-all duration-300 ease-initial">
          <img src="/cards/card-7.svg" class="w-full h-full object-cover" alt="">
          <div class="absolute z-10 top-0 left-0 w-full h-full flex flex-col p-4 items-center justify-center gap-4">
            <img src="/icons/figma.svg" alt="" class="w-16 pb-8">
            <h4 class="text-white shadow-2xl text-4xl text-center font-b">UI / UX Design</h4>
            <p class="text-zinc-200 text-lg text-center font-light">From wireframes to final visuals, I create smooth, modern designs your users will love.</p>
          </div>
        </div> 
        <div class=" snap-start w-84 xl:w-full h-96 flex-shrink-0 rounded-2xl overflow-hidden relative hover:scale-[1.02] hover:-translate-y-6 transition-all duration-300 ease-initial">
          <img src="/cards/card-8.svg" class="w-full h-full object-cover" alt="">
          <div class="absolute  z-10 top-0 left-0 w-full h-full flex flex-col p-4 items-center justify-center gap-4">
            <div class=" z-20 absolute w-full h-full bg-gradient-to-t from-black via-transparent to-transparent"></div>
            <h4 class="text-white shadow-2xl text-4xl w-full text-left font-b">Design System</h4>
            <p class="text-zinc-200 text-shadow-md text-lg text-left font-light">I create flexible websites powered by cutting-edge tools and modern frameworks.</p>
            <img src="/extra/bracket.svg" alt="" class="w-16 pt-8">

          </div>
        </div>
        
        <div class=" snap-start w-84 xl:w-full h-96 flex-shrink-0 rounded-2xl overflow-hidden relative hover:scale-[1.02] hover:-translate-y-6 transition-all duration-300 ease-initial">
          <img src="/cards/card-4.svg" class="w-full h-full object-cover" alt="">
          <div class="absolute z-10 top-0 left-0 w-full h-full flex flex-col p-4 items-center justify-center gap-4">
            <img src="/extra/home.svg" alt="" class="w-16 pb-8">
            <h4 class="text-white shadow-2xl text-4xl text-center font-b">Branding</h4>
            <p class="text-zinc-200 text-shadow-md text-lg text-center font-normal">I help you create a strong visual identity — from logos to colors — that makes your brand stand out.</p>
          </div>
        </div> 
        
    </div>
</div>



<style>
    .hide-scrollbar::-webkit-scrollbar {
        display: none;
    }

  .hide-scrollbar {
    -ms-overflow-style: none;
    scrollbar-width: none;
  }
</style>