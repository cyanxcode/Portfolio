<script lang="ts">
	import { goto } from "$app/navigation";
    import { onMount } from "svelte";

    let {type= "square", img, title, description} = $props();
    let isMobile = $state(false);

    switch (type) {
        case "square":
            type= "aspect-square"
            break
        case "tall":
            type= "md:row-span-2"
            break
        case "wide":
            type= "md:col-span-2"
            break
        default:
            type= "aspect-square"
    }


    function checkSize() {
        isMobile = window.innerWidth > 768;
    }

    onMount(() => {
        checkSize();
        window.addEventListener('resize', checkSize);

        return () => {
            window.removeEventListener('resize', checkSize);
        };
    });
    const handleClick = async () =>  {
        await new Promise(resolve => setTimeout(resolve, 400));
        goto('/work/' + title);
    }
</script>


<button data-cursor="icon" class={`${type} parent cursor-none w-full h-full overflow-hidden rounded-2xl object-cover relative group`} onclick={handleClick}>
    <img src={img} alt={title} class={`w-full h-full object-cover effect transition-all duration-300 ease-in-out`}>

    <div class={` absolute w-full h-full top-0 left-0 z-20 bg-gradient-to-t p-5 from-black lg:opacity-0 lg:group-hover:opacity-100 transition-all duration-300 ease-in-out`}>
      <div class="flex flex-col items-start justify-end h-full gap-2 text-left ">
        <h4 class="text-2xl tracking-wider lg:text-3xl karantina text-white whitespace-nowrap">{title}</h4>
        <p class="text-zinc-300 text-sm ml-2 truncate whitespace-nowrap w-[90%]">{description}</p>
      </div>
    </div>
</button>

<style>
    @media (hover:hover) {
        .effect {
            filter: blur(8px);
            transition: all 0.3s ease-in-out;
        }
        .parent:hover .effect {
            filter: blur(0px);
        }
    }

    @media (hover:none) {
        .effect {
            filter: blur(0px);
        }
    }
</style>