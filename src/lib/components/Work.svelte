<script lang="ts">
	import { goto } from "$app/navigation";
	import WorkItems from "./WorkItems.svelte";
  import { onMount } from "svelte";
  import gsap from "gsap";
  import { ScrollTrigger } from "gsap/all";

    let textEl: any;
   let text = "MY WORK";
   let splitText = text.split("");

  function handleClick() {
    goto("/work");
  }
  onMount(() => {
 
    gsap.registerPlugin(ScrollTrigger);
    let chars = textEl.querySelectorAll('.char');

    gsap.from(chars, {
      scrollTrigger: {
      trigger: textEl,
      start: 'top 80%',
    },
    y: 30,
    opacity: 0,
    stagger: 0.05,
    ease: 'power2.out',
  });
  })
</script>
<div class="" data-cursor="asteroid">
  <div class="w-full flex justify-end mt-8">
    <h1 bind:this={textEl} class="karantina relative text-right py-10 px-6 sm:px-8 md:px-20 text-white text-4xl sm:text-5xl md:text-7xl lg:text-8xl leading-tight uppercase">
      <img src="/icons/helmet.svg" alt="" class="w-16 md:24 lg:w-32 absolute z-30 top-0 -left-2 sm:top-1 sm:left-1 md:top-3 md:left-14 lg:-top-6 -rotate-12 lg:left-7">
       {#each splitText as char, i}
              <span class="char">{char == ' '? '\u00A0': char}</span>
        {/each}
    </h1></div>
  
  <div class="grid grid-cols-1 md:grid-cols-3 px-6 md:px-24 gap-4">
    <WorkItems type="tall" img="/work/Apple3.png" title="Apple Website Recreated" description="Showcasing iPhone 15 Pro"/>    
    <WorkItems type="wide" img="/work/Amprio.png" title="Amprio" description="A full-fledged ecommerce store for a lighting brand"/>
    <WorkItems type="square" img="/work/Cybercup.png" title="Cybercup" description="Designed the Website for National Level Hackathon"/>
    <WorkItems type="square" img="/work/Realm.png" title="Realm" description="Developed an AI search engine"/>


  
  </div>
<button data-cursor="click" onclick={handleClick} class="my-10 hover:scale-105 flex items-center justify-center gap-3 px-2 py-2 rounded-full font-bold bg-white  ml-[50%] -translate-x-1/2 transition-all duration-300 ease-in-out">
    <p class="ml-4 mr-2">Show all</p>
    <img src="/extra/arrow-black-r.svg" class="w-8 hidden" alt="">
    <div class="bg-black rounded-full w-10 h-10 grid place-content-center">
        <img src="/extra/arrow-right.svg" class="w-8" alt="">
    </div>

</button>
</div>  