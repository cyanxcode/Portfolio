<script lang="ts">
    import { onMount } from 'svelte';
  
    let x = $state(0);
    let y = $state(0);
    let variant: keyof typeof variants = $state('close');
    let isFinePointer = $state(true); // Assume mouse until proven otherwise
  
    const variants = {
      close: 'hidden',
      default: 'w-4 h-4 bg-white',
      large: 'w-12 h-12 bg-white',
      click: 'w-12 h-12 bg-white flex items-center justify-center text-xs',
      icon: 'w-12 h-12 bg-white text-white flex items-center justify-center text-xs',
    };
  
    let lastTarget: EventTarget | null = null;
  
    function updateCursorVariant(target: EventTarget | null) {
      if (!isFinePointer) return;
  
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
  
    onMount(() => {
      isFinePointer = window.matchMedia('(pointer: fine)').matches;
  
      if (!isFinePointer) {
        variant = 'close';
        return;
      }
  
      function handlePointerMove(e: PointerEvent) {
        if (e.pointerType !== 'mouse') return;
  
        x = e.clientX;
        y = e.clientY;
        lastTarget = e.target;
        updateCursorVariant(lastTarget);
      }
  
      function handleScroll() {
        if (!isFinePointer) return;
  
        const hovered = document.elementFromPoint(x, y);
        updateCursorVariant(hovered);
      }
  
      window.addEventListener('pointermove', handlePointerMove);
      window.addEventListener('scroll', handleScroll, true);
  
      return () => {
        window.removeEventListener('pointermove', handlePointerMove);
        window.removeEventListener('scroll', handleScroll, true);
      };
    });
  </script>
  
  {#if isFinePointer}
    <!-- Cursor only renders on fine pointer (mouse/trackpad) -->
    <div
      class={`pointer-events-none fixed top-0 left-0 z-[9999] rounded-full transition-all duration-[40] ease-in-out transform ${variants[variant]}`}
      style={`transform: translate(calc(${x}px - 50%), calc(${y}px - 50%));`}
    >
      {#if variant === 'icon'}
        <img src="/extra/arrow-up-right.svg" alt="" class="w-6 h-6" />
      {/if}
      {#if variant === 'click'}
        <p>Click</p>
      {/if}
    </div>
  {/if}