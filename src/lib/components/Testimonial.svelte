<script lang="ts">

  import { onMount } from "svelte";
  import gsap from "gsap";
  import { ScrollTrigger } from "gsap/all";

   let textEl: any;
   let text = "Testimonial";
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
    ease: 'power2.out',
  });
  })
    const testimonials = [
      {
        name: "Dr. Shilpi Sharma",
        title: "Dept HOD",
        company: "Amity University",
        img: "/img/testimonial1.jpeg",
        quote: "I am confident that Avijit Verma has the intellectual capabilities, motivation and determination required to succeed in his future endeavors. I am certain that he will contribute positively to any organization."
      },
      {
        name: "Rudrakshi Aggarwal",
        title: "Co Founder",
        company: "Amprio",
        img: "/img/testimonial2.jpeg",
        quote: "Good work and great communication skills, can fit in any environment and have exceptional technical knowledge."
      },
    ];
  </script>
<div class="flex items-end py-10 gap-4">
    <h1 bind:this={textEl} class="karantina text-left pl-4 sm:pl-8 md:pl-20 text-white text-4xl sm:text-5xl md:text-7xl lg:text-8xl leading-tight uppercase">
        {#each splitText as char}
      <span class="char">{char == ' '? '\u00A0': char}</span>
      {/each}
    </h1>
    <img src="/icons/bb8.svg" alt="" class=" -ml-5 w-20 md:w-40">
</div>
<div class="flex flex-col items-center w-full space-y-6 px-4 sm:px-8 md:px-20">
    {#each testimonials as testimonial}
    <div class="w-full bg-white text-black md:bg-black md:text-white md:hover:bg-white md:hover:text-black transition-colors duration-300 group rounded-xl p-4 sm:p-6 flex flex-col md:flex-row md:items-center gap-4">
        
        <!-- Profile Section -->
        <div class="flex md:w-[40%] w-full items-center gap-4">
            <div class="w-14 h-14 sm:w-16 sm:h-16 rounded-full bg-black md:bg-white md:group-hover:bg-black shrink-0 overflow-hidden">
                <img src={testimonial.img} alt={testimonial.name} class="w-full h-full object-cover rounded-full">
            </div>
            <div class="flex flex-col">
                <p class="text-lg sm:text-xl font-medium leading-tight">{testimonial.name}</p>
                {#if testimonial.title}
                    <p class="text-sm sm:text-base text-zinc-600 md:text-zinc-300 md:group-hover:text-zinc-600">{testimonial.title}</p>
                {/if}
                {#if testimonial.company}
                    <p class="text-sm sm:text-base text-zinc-600 md:text-zinc-300 md:group-hover:text-zinc-600">{testimonial.company}</p>
                {/if}
            </div>
        </div>

        <!-- Quote -->
        <p class="text-base sm:text-lg md:text-xl italic font-semibold md:w-[60%] w-full">
            “{testimonial.quote}”
        </p>
    </div>

    <!-- Divider -->
    {#if !(testimonials[testimonials.length - 1] === testimonial)}
    <div class="w-full h-[1px] bg-zinc-300"></div>
    {/if}
    {/each}
</div>