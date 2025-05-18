<script lang="ts">
    import { onMount } from "svelte";
    import { gsap } from "gsap";
    import CursorEffect from "$lib/components/CursorEffect.svelte";
  
  
    let textEL: any;
    onMount(() => {
      const chars = textEL.querySelectorAll('.char');
  
      gsap.from(chars, {
        opacity: 0,
        y: 60,
        stagger: 0.1,
        duration: 1
      });
    });
    let text = "CYAN STUDIOS";
    let splitText = text.split("");
</script>

<CursorEffect extraClass="grid place-items-center">

    <iframe
    src="https://my.spline.design/claritystream-D6CXXIB05mBhwdSjo6fw0m9z/"
    title="3D Scene"
    frameborder="0"
    width="100%"
    height="100%"
    style="border: none; "
    class="absolute top-0 left-0 w-full h-[50vw] md:h-full pointer-events-none"
    >
  </iframe>
  <div class="w-40 h-12 bg-black z-10 absolute right-2 top-[calc(50vw-4rem)] md:top-auto md:bottom-5 rounded-xl"></div>

  <div class="h-auto lg:h-screen box-border py-24 w-full grid place-items-center relative px-4 md:px-10">

      <div class="relative z-10 w-full flex flex-row justify-end items-center pr-5 md:px-10 lg:px-24 gap-6">
        <!-- Text Section -->
        <div class="text-right">
          <h1 bind:this={textEL} class="karantina text-white text-7xl sm:text-9xl md:text-[9rem] lg:text-[10rem] xl:text-[12rem] leading-none">
            {#each splitText as char, i}
              {#if (i == 4)}
              <br>
              {:else}
              <span class="char">{char}</span>
              {/if}
            {/each}
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

<style>
    .char {
      display: inline-block;
    }
</style>