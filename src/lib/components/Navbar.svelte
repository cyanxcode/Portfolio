<script>
    let isOpen = $state(false);
</script>

<nav class={`${isOpen ? 'top-0': '-top-[3rem]'} absolute flex flex-col w-full z-50 items-center transition-all duration-100 ease-in-out`}>
    <div class="w-full h-12 bg-white flex items-center justify-evenly">
        <a href="#x" class="uppercase karantina text-xl sm:text-3xl">Home</a>
        <a href="#x" class="uppercase karantina text-xl sm:text-3xl">About</a>
        <div class="hidden md:block"></div>
        <a href="#x" class="uppercase karantina text-xl sm:text-3xl">Work</a>
        <a href="#x" class="uppercase karantina text-xl sm:text-3xl">Pricing</a>
    </div>
    <button onclick={() => isOpen = !isOpen} class="poly z-50">
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