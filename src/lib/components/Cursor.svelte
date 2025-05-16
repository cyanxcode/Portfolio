<script lang="ts">
    import { onMount } from 'svelte';
  
    let x = $state(0);
    let y = $state(0);
    let variant: keyof typeof variants = $state('close');
    let isTouch = $state(false);

    function handleTouchStart() {
        isTouch = true;
        variant = 'close'; // Hide cursor
    }
  
    const variants = {
      close: 'hidden',
      default: 'w-4 h-4 bg-white cursor-pointer',
      large: 'w-12 h-12 bg-white',
      click: 'w-12 h-12 bg-white flex items-center justify-center text-xs',
      icon: 'w-12 h-12 bg-white text-white flex items-center justify-center text-xs',
    };
  
    function updateCursorVariant(target: EventTarget | null) {
      let el = target as HTMLElement | null;
      let foundCursor = false;
  
      while (el && el !== document.body) {
        const cursorType = el.dataset?.cursor;
        if (cursorType) {
          variant = cursorType as keyof typeof variants;
          foundCursor = true;
          break;
        }
        el = el.parentElement;
      }
  
      if (!foundCursor) {
        variant = 'close';
      }
    }
  
    function handleMove(e: MouseEvent) {
      x = e.clientX;
      y = e.clientY;
      updateCursorVariant(e.target);
    }
  
    function handleScroll() {
      const hovered = document.elementFromPoint(x, y);
      updateCursorVariant(hovered);
    }
    onMount(() => {
        window.addEventListener('mousemove', handleMove);
        window.addEventListener('scroll', handleScroll, true);
        window.addEventListener('touchstart', handleTouchStart, { once: true });

        return () => {
            window.removeEventListener('mousemove', handleMove);
            window.removeEventListener('scroll', handleScroll, true);
            window.removeEventListener('touchstart', handleTouchStart);
        };
});
  </script>
  
  <!-- Cursor -->
  <div
    class={`pointer-events-none fixed top-0 left-0 z-[9999] rounded-full transition-all duration-[40] ease-in-out transform ${variants[variant]}`}
    style={`transform: translate(calc(${x}px - 50%), calc(${y}px - 50%));`}
  >
    {#if variant === 'icon'}
      <img src="/extra/arrow-up-right.svg" alt="" class="w-6 h-6" />
    {/if}
    {#if variant === 'click'}
        <p class="">Click</p>
    {/if}
  </div>