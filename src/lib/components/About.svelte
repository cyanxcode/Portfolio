<script lang="ts">
   import { onMount } from 'svelte';
   import gsap from 'gsap';
   import { ScrollTrigger } from 'gsap/ScrollTrigger';
   import { browser } from '$app/environment';

   let textEL: any;
   let paraEl: any;
   let text = "ABOUT AVIJIT VERMA";
   let splitText = text.split("");
 
   let isScrolling = $state(false);
   let timeout: ReturnType<typeof setTimeout>;
 
   let marqueeEl: HTMLDivElement;
   let offset = $state(0);
   let direction = $state(1);
   let speed = 1.4;
   let bounceFactor = 0.1; 
   let bounceState = $state(0);


 
   const handleScroll = () => {
     isScrolling = true;
     direction = -1; // Reverse on scroll
     clearTimeout(timeout);
     timeout = setTimeout(() => {
       isScrolling = false;
       direction = 1; // Resume rightward scroll
     }, 100);
   };
 
   onMount(() => {
    if (!browser) return;
    gsap.registerPlugin(ScrollTrigger);
   const animate = () => {
     if (isScrolling) {
       // When scrolling, add bounce to the direction change
       bounceState += bounceFactor;  // Increase the bounce effect slightly
       
       // Apply bounce, but after the bounce, make sure the animation continues smoothly.
       offset += direction * speed * (1 + Math.sin(bounceState));

       // Once the bounce effect finishes, reset it to allow smooth movement.
       if (Math.abs(Math.sin(bounceState)) < 0.1) {
         bounceState = 0;
       }
     } else {
       offset += direction * speed;
     }
 
     // Loop back seamlessly
  const totalWidth = marqueeEl.scrollWidth / 3;

if (direction === -1 && offset <= -totalWidth) {
  offset = 0;
}
if (direction === 1 && offset >= 0) {
  offset = -totalWidth;
}

     marqueeEl.style.transform = `translateX(${offset}px)`;
     requestAnimationFrame(animate);
   };
 
    let chars = textEL.querySelectorAll('.char');

    gsap.from(chars, {
      scrollTrigger: {
      trigger: textEL,
      start: 'top 80%',
    },
    y: 30,
    opacity: 0,
    stagger: 0.05,
    ease: 'power2.out',
  });
  gsap.from(paraEl, {
    scrollTrigger: {
      trigger: paraEl,
      start: 'top 80%',
    },
    y: 30,
    opacity: 0,
    duration: 1,
   });

    requestAnimationFrame(animate);
   });
 </script>
 
 <svelte:window on:scroll={handleScroll} />
 <main class="w-full py-10" data-cursor="asteroid">
  <div class="w-full grid grid-cols-2 px-3 md:px-10 lg:px-16 relative ">
    

    <div class="flex md:justify-end justify-center">
      <img src="/img/profile.jpeg" alt="Avijit Verma" class="w-full max-w-md h-[22rem] md:h-[26rem] lg:h-[30rem] object-cover rounded-lg shadow-md" />
    </div>
    <!-- Text Section -->
    <div class="flex flex-col text-left items-start p-4 md:p-8 gap-1 md:gap-6">
      <h1 bind:this={textEL} class="karantina text-left text-white text-5xl md:text-7xl lg:text-8xl leading-tight uppercase whitespace-nowrap">
        {#each splitText as char, i}
            {#if (i == 5)}
              <br>
            {:else}
              <span class="char">{char == ' '? '\u00A0': char}</span>
            {/if}
        {/each}
      </h1>
      <p bind:this={paraEl} class="text-white font-extralight text-sm sm:text-base md:text-lg lg:text-xl max-w-md">
        I am a full-stack developer who turns bold ideas into reality. 
        I specialize in blending code with modern design to craft applications that don't just look great - but perform.
      </p>
    </div>

    <!-- Image -->

    <!-- Button with Arc Text -->
    <a href="https://rxresu.me/codinginstant/cyan" target="_blank"
      data-cursor="icon"
      class="hover:scale-105 cursor-none absolute z-10 left-1/2 -translate-y-1/2 -translate-x-1/2 top-full w-28 md:w-32 aspect-square border-[10px] md:border-[12px] border-black rounded-full bg-blue-600 text-white font-medium transition-all duration-300 ease-in-out">
      
      <!-- Arc Text SVG -->
      <svg class="absolute inset-0 w-full h-full -mt-2" viewBox="0 0 100 100">
        <defs>
          <path id="arcPath" d="M10,60 A40,40 0 0,1 90,60" />
        </defs>
        <text fill="white" font-size="10" font-weight="400" style="letter-spacing: 1px;">
          <textPath href="#arcPath" startOffset="50%" text-anchor="middle">
            GET MY RESUME
          </textPath>
        </text>
      </svg>
      <img src="/extra/arrow-top-r.svg" alt="" class="w-8 md:w-10 left-1/2 absolute -translate-1/2 top-1/2" />
    </a>
  </div>

  <!-- ✅ Marquee Section -->
  <div class="bg-zinc-200 overflow-hidden h-28 md:h-36 mt-4 mb-24">
    <div bind:this={marqueeEl} class="flex h-full w-max whitespace-nowrap animate-scroll">
      {#each Array(3) as _}
        <div class="flex items-center justify-between gap-16 md:gap-32 h-full text-black px-6">
          <img src="/extra/star4.svg" alt="" class="w-4 md:w-6" />
          <h1 class="text-3xl md:text-4xl lg:text-5xl karantina text-center">Web Developer</h1>
          <img src="/extra/star4.svg" alt="" class="w-4 md:w-6" />
          <h1 class="text-3xl md:text-4xl lg:text-5xl karantina text-center">UI Designer</h1>
          <img src="/extra/star4.svg" alt="" class="w-4 md:w-6" />
          <h1 class="text-3xl md:text-4xl lg:text-5xl karantina text-center">Engineer</h1>
        </div>

        <div class="w-4 md:w-20"></div>
      {/each}
    </div>
  </div>
</main>