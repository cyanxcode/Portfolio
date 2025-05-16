<script>
    import { getContext } from 'svelte';
    let { children } = $props();
    const id = getContext('item');
    const { toggle } = getContext('accordion');
  </script>
  
  <button
    onclick={() => toggle(id)}
    class="w-full text-left font-medium cursor-pointer"
  >
    <div class="flex justify-between">
        {@render children()}
        <img src="/extra/arrow-right.svg" class="w-6" alt="">
    </div>
  </button>