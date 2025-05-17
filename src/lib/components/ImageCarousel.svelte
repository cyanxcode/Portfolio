<script lang="ts">
  
    export let images: any = ["/work/Amprio.png", "/work/Amprio.png", "/work/Amprio.png", "/work/Amprio.png"];
  
    let currentIndex = 0;
  
    let startX = 0;
    let currentX = 0;
    let isDragging = false;
  
    function prev() {
      currentIndex = (currentIndex - 1 + images.length) % images.length;
    }
  
    function next() {
      currentIndex = (currentIndex + 1) % images.length;
    }
  
    function touchStart(event: any) {
      isDragging = true;
      startX = event.touches[0].clientX;
    }
  
    function touchMove(event: any) {
      if (!isDragging) return;
      currentX = event.touches[0].clientX;
    }
  
    function touchEnd() {
      if (!isDragging) return;
      let diff = currentX - startX;
      if (diff > 50) {
        prev();
      } else if (diff < -50) {
        next();
      }
      isDragging = false;
      startX = 0;
      currentX = 0;
    }
  </script>
  
  <div class="relative w-full max-w-xl mx-auto select-none">
    <!-- Images container -->
    <div
      class="overflow-hidden rounded-lg"
      ontouchstart={touchStart}
      ontouchmove={touchMove}
      ontouchend={touchEnd}
    >
      <div
        class="flex transition-transform duration-500 ease-in-out"
        style="transform: translateX(-{currentIndex * 100}%)"
      >
        {#each images as img}
          <img src={img} alt="" class="w-full aspect-square flex-shrink-0 object-cover" />
        {/each}
      </div>
    </div>
  
  
    <!-- Dots -->
    <div class="absolute bottom-2 left-1/2 -translate-x-1/2 flex justify-center mt-4 space-x-2">
      {#each images as _, i}
        <button
          onclick={() => (currentIndex = i)}
          class="w-3 h-3 rounded-full transition-colors"
          class:selected={i === currentIndex}
          style="background-color: {i === currentIndex ? '#000' : '#bbb'}"
          aria-label={`Go to slide ${i + 1}`}
        ></button>
      {/each}
    </div>
  </div>
  
  <style>
  </style>