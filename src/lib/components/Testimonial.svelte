<script>
    const testimonials = [
      {
        name: "Dr. Shilpi Sharma",
        title: "Dept HOD",
        company: "Amity University",
        quote: "Good work and great communication skills, can fit in any environment and have exceptional technical knowledge."
      },
      {
        name: "Rudrakshi Aggarwal",
        title: "Co Founder",
        company: "Ampro",
        quote: "Good work and great communication skills, can fit in any environment and have exceptional technical knowledge."
      },
    ];
  </script>

<h1 class="karantina text-left py-10 px-4 sm:px-8 md:px-20 text-white text-4xl sm:text-5xl md:text-7xl lg:text-8xl leading-tight uppercase">
    Testimonials
</h1>
<div class="flex flex-col items-center w-full space-y-6 px-4 sm:px-8 md:px-20">
    {#each testimonials as testimonial}
    <div class="w-full bg-white text-black md:bg-black md:text-white md:hover:bg-white md:hover:text-black transition-colors duration-300 group rounded-xl p-4 sm:p-6 flex flex-col md:flex-row md:items-center gap-4">
        
        <!-- Profile Section -->
        <div class="flex md:w-[40%] w-full items-center gap-4">
            <div class="w-14 h-14 sm:w-16 sm:h-16 rounded-full bg-black md:bg-white md:group-hover:bg-black shrink-0"></div>
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