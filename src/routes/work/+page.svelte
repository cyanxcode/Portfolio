<script lang="ts">

import WorkItems from "$lib/components//WorkItems.svelte";
  import { onMount } from "svelte";
  import gsap from "gsap";
  import { ScrollTrigger } from "gsap/all";

   let textEl: any;
   let text = "MY WORK";
   let splitText = text.split("");
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
    delay: 0.8,
    ease: 'power2.out',
  });
  })

</script>

<svelte:head>
	<title>My Work</title>
</svelte:head>
<div class="" data-cursor="asteroid">
  <div class="w-full flex items-center justify-between mt-8 py-10 px-12 md:px-20">
    <a href="/">
      <img src="/extra/left-w.svg" class="w-8 lg:w-12 hover:scale-120 transition-all duration-200 ease-in-out" alt="">
    </a>
    <h1 bind:this={textEl} class="karantina relative text-right  text-white text-4xl sm:text-5xl md:text-7xl lg:text-8xl leading-tight uppercase">
      <img src="/icons/helmet.svg" alt="" class="w-16 md:24 lg:w-32 absolute z-30 -top-9 -left-7 sm:-top-8 sm:-left-7 md:-top-4 md:-left-6 lg:-top-14 -rotate-12 lg:-left-12">
      {#each splitText as char}
      <span class="char">{char == ' '? '\u00A0': char}</span>
{/each}
    </h1></div>
  
  <div class="grid grid-cols-1  md:grid-cols-3 px-12 md:px-24 gap-4 pb-40">
    <WorkItems type="tall" img="/work/Apple3.png" title="Apple Website Recreated" description="Showcasing iPhone 15 Pro"/>    
    <WorkItems type="wide" img="/work/Amprio.png" title="Amprio" description="A full-fledged ecommerce store for a lighting brand"/>
    <WorkItems type="square" img="/work/Cybercup.png" title="Cybercup" description="Designed the Website for National Level Hackathon"/>
    <WorkItems type="square" img="/work/Realm.png" title="Realm" description="Developed an AI search engine"/>


  
  </div>
</div>  