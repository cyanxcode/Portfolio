<script>
    let isOpen = $state(false);
</script>

<nav class={`${isOpen ? 'top-0': '-top-[3rem]'} absolute flex flex-col w-full z-50 items-center transition-all duration-100 ease-in-out`}>
    <div class="w-full h-12 bg-white flex items-center justify-evenly font-medium text-base sm:text-lg">
        <a target="_blank" href="https://www.instagram.com/lifeofavijit" class="flex gap-2 items-center"><img src="/icons/instagram.svg" alt="" class="w-6 md:w-8"><p class="hidden md:block">Instagram </p></a>
        <a target="_blank" href="https://www.linkedin.com/in/avijit-verma-2abb962a5" class="flex gap-2 items-center"><img src="/icons/linkedin.svg" alt="" class="w-6 md:w-8"><p class="hidden md:block">LinkedIn </p></a>
        <div class="hidden md:block"></div>
        <a target="_blank" href="/404" class="flex gap-2 items-center"><img src="/icons/dribbble.svg" alt="" class="w-6 md:w-8"><p class="hidden md:block">Dribbble </p></a>
        <a target="_blank" href="/404" class="flex gap-2 items-center"><img src="/icons/x.svg" alt="" class="w-6 md:w-8"><p class="hidden md:block">x.com </p></a>
    </div>
    <button onclick={() => isOpen = !isOpen} class="poly z-50  cursor-pointer">
        <img src="/extra/menu2.svg" class="w-6 ml-[50%] mt-3 -translate-1/2" alt="">
    </button>
</nav>



<style>
    .poly{
        width: 10rem;
        height: 1.5rem;
        background-color: #fff;
        clip-path: polygon(0 0, 100% 0, 90% 100%, 10% 100%);
    }
</style>