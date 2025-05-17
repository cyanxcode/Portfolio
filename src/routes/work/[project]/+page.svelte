<script>
    import { data } from "$lib/data";
    import { page } from '$app/stores';
	import ImageCarousel from "$lib/components/ImageCarousel.svelte";

    let work = data.find((item) => item.title.toLowerCase() === $page.params.project.toLowerCase());
</script>

{#if work}
<main class="flex flex-col gap-4 px-8 sm:px-10 md:px-20 lg:px-40 xl:px-60 mt-4 md:mt-16 mb-20">

    <div class="flex gap-4 sm:gap-10 items-center pt-20">
        <a href="/work">
            <img src="/extra/left-w.svg" class="w-6 sm:w-8 hover:scale-110 transition-all duration-200 ease-in-out" alt="">
        </a>
        <h2 class="text-2xl sm:text-3xl text-white font-medium text-left">{work.title}</h2>
    </div>
    <div class="md:hidden block">
        <ImageCarousel images={work.img}/>
    </div>
    <div class="w-full md:grid hidden md:grid-cols-4 md:grid-rows-2 gap-3">
        <div class="md:col-span-2 md:row-span-2 aspect-square rounded-lg overflow-hidden bg-red-100">
            <img src={work.img[0]} alt="" class="w-full h-full hover:scale-105 transition-all duration-200 ease-in-out object-cover">
        </div>
        {#each Array(work.img.length - 1) as _, i}
            <div class="aspect-square hidden md:block rounded-lg overflow-hidden">
                <img src={work.img[i + 1]} alt="" class="w-full h-full hover:scale-105 transition-all duration-200 ease-in-out object-cover">
            </div>
        {/each}
    </div>

    <p class="text-zinc-400 text-base sm:text-lg font-light mt-6 sm:mt-10">
        {work.description}
    </p>

    {#each work.section as section}
        <h3 class="text-lg sm:text-xl font-semibold text-white mt-4 sm:mt-5">{section.title}</h3>

            <ul class="list-disc pl-6 text-inde ml-6">
                <p class="text-zinc-400 text-base sm:text-lg font-light">
                    {@html section.content}
                </p>
            </ul>
    {/each}

    <div class="flex flex-row gap-4 py-6">
        {#if work.website}
        <a href={work.website} target="_blank" 
        class="text-black text-base sm:text-lg font-semibold flex items-center justify-center rounded-sm bg-white py-2 w-[50%] sm:w-36 hover:bg-zinc-200 transition-all duration-200 ease-in-out">
            Website
        </a>
        {/if}
        {#if work.github}
        <a href={work.github} target="_blank" 
        class="text-white text-base sm:text-lg border box-content border-white gap-2 font-semibold flex items-center justify-center rounded-sm bg-black py-2 w-[50%] sm:w-36 hover:bg-zinc-800 transition-all duration-200 ease-in-out">
            <img src="/icons/github.svg" class="w-5" alt="">
            Github
        </a>
        {/if}
    </div>
</main>

{:else}
<div class="w-full h-screen flex flex-col items-center justify-center px-4">
    <h2 class="text-2xl sm:text-3xl text-white font-medium text-center">404 <span class="ml-4">Work not found</span></h2>
</div>
{/if}