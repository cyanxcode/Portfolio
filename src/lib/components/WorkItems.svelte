<script>
    let {type= "square", img, title, description, link = ""} = $props();
    let isOpen = $state(false);
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
    function handleClick() {
        if (!isOpen) {
            isOpen = true;
        } else {
            // Go to the link
        }
    }
</script>


<button class={`${type} w-full h-full overflow-hidden rounded-2xl object-cover relative group`} onclick={handleClick}>
    <img src={img} alt={title} class={`w-full h-full object-cover md:blur-md md:group-hover:blur-none ${isOpen ? "blur-none" : 'blur-md'} transition-all duration-300 ease-in-out`}>
    <div class={`absolute w-full h-full top-0 left-0 z-20 bg-gradient-to-t p-5 from-black md:opacity-0 md:group-hover:opacity-100 ${isOpen ? "opacity-100" : "opacity-0"} transition-all duration-300 ease-in-out`}>
      <div class="flex flex-col items-start justify-end h-full gap-4">
        <h4 class="text-xl sm:text-2xl md:text-3xl karantina text-white">{title}</h4>
        <p class="text-zinc-300 text-sm ml-2">{description}</p>
      </div>
    </div>
</button>