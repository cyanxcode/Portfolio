<script lang="ts">
   import { onMount } from 'svelte';
 
   let isScrolling = $state(false);
   let timeout: ReturnType<typeof setTimeout>;
 
   let marqueeEl: HTMLDivElement;
   let offset = $state(0);
   let direction = $state(1);
   let speed = 1;
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
  const totalWidth = marqueeEl.scrollWidth / 2;

if (direction === -1 && offset <= -totalWidth) {
  offset = 0;
}
if (direction === 1 && offset >= 0) {
  offset = -totalWidth;
}

     marqueeEl.style.transform = `translateX(${offset}px)`;
     requestAnimationFrame(animate);
   };
 
   onMount(() => {
     requestAnimationFrame(animate);
   });
 </script>
 
 <svelte:window on:scroll={handleScroll} />
 <main class="w-full my-10" data-cursor="default">
  <div class="w-full grid grid-cols-2 px-3 md:px-10 lg:px-16 relative ">
    

    <div class="flex md:justify-end justify-center">
      <img src="/img/profile.jpeg" alt="Avijit Verma" class="w-full max-w-md h-[22rem] md:h-[26rem] lg:h-[30rem] object-cover rounded-lg shadow-md" />
    </div>
    <!-- Text Section -->
    <div class="flex flex-col text-left items-start p-4 md:p-8 gap-1 md:gap-6">
      <h1 class="karantina text-left text-white text-5xl md:text-7xl lg:text-8xl leading-tight uppercase whitespace-nowrap">
        About <br /> Avijit Verma
      </h1>
      <p class="text-white font-extralight text-sm sm:text-base md:text-lg lg:text-xl max-w-md">
        I am a full-stack developer who turns bold ideas into reality. 
        I specialize in blending code with modern design to craft applications that don't just look great - but perform.
      </p>
    </div>

    <!-- Image -->

    <!-- Button with Arc Text -->
    <button
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
    </button>
  </div>

  <!-- ✅ Marquee Section -->
  <div class="bg-zinc-200 overflow-hidden h-28 md:h-36 mt-4 mb-24">
    <div bind:this={marqueeEl} class="flex h-full w-max whitespace-nowrap animate-scroll">
      {#each Array(2) as _}
        <div class="flex items-center justify-between gap-4 md:gap-6 w-[100vw] h-full text-black px-6">
          <h1 class="text-3xl md:text-4xl lg:text-5xl karantina text-center">Web Developer</h1>
          <img src="/extra/star4.svg" alt="" class="w-4 md:w-6" />
          <h1 class="text-3xl md:text-4xl lg:text-5xl karantina text-center">UI Designer</h1>
          <img src="/extra/star4.svg" alt="" class="w-4 md:w-6" />
          <h1 class="text-3xl md:text-4xl lg:text-5xl karantina text-center">Engineer</h1>
          <img src="/extra/star4.svg" alt="" class="w-4 md:w-6" />
        </div>
      {/each}
    </div>
  </div>
</main>