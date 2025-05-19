<script lang="ts">
	import Accordian from "./Accordian/Accordian.svelte";
	import AccordianContent from "./Accordian/AccordianContent.svelte";
	import AccordianIteam from "./Accordian/AccordianIteam.svelte";
	import AccordianTrigger from "./Accordian/AccordianTrigger.svelte";


  import { onMount } from "svelte";
  import gsap from "gsap";
  import { ScrollTrigger } from "gsap/all";

   let textEl: any;
   let text = "FAQs";
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

    const faqs = [
  {
    question: "What’s your workflow like?",
    answer: "I start by understanding your goals, then move into wireframes and design mockups. Once approved, I build, test, and iterate — with continuous feedback loops throughout."
  },
  {
    question: "Do you do both design and development?",
    answer: "Yes! I bridge the gap between design and code. You don’t need to hire separate designers and developers — I handle both."
  },
  {
    question: "What’s your typical project timeline?",
    answer: "Most projects take 4–6 weeks, depending on complexity. I’ll give you a custom timeline after our first conversation."
  },
  {
    question: "What do you charge?",
    answer: "Pricing depends on the project scope, but I usually offer fixed-rate packages. After a quick call, I’ll send over a custom quote."
  },
  {
    question: "Do you offer post-launch support?",
    answer: "Yes. I offer maintenance packages and can help with future updates or performance improvements."
  }
];

</script>

<div bind:this={textEl} class="flex w-full justify-center py-6 gap-4">
    <h1 class="karantina text-right pl-4 sm:pl-8 md:pl-20 text-white text-4xl sm:text-5xl md:text-7xl lg:text-8xl leading-tight uppercase">
      {#each splitText as char}
      <span class="char">{char == ' '? '\u00A0': char}</span>
      {/each}
    </h1>
</div>
<div class="text-white flex flex-col items-center pb-20">
    <Accordian type="single" extraClass="w-full md:w-[70%] px-10">
        {#each faqs as faq}
        <AccordianIteam>
            <AccordianTrigger>
                <p class="">{faq.question}</p>
            </AccordianTrigger>
            <AccordianContent>
                <p class="font-light px-2">{faq.answer}</p>
            </AccordianContent>
        </AccordianIteam>
        {/each}
    </Accordian>
</div>