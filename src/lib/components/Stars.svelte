<script>
    const particleCount = 30;
    const particles = Array.from({ length: particleCount }, (_, i) => ({
      id: i,
      x: Math.random() * 100,
      y: Math.random() * 100,
      size: Math.random() * 2 + 1,
      delay: Math.random() * 5,
      duration: Math.random() * 10 + 10
    }));
  </script>
  
  <div class="fixed inset-0 -z-20 overflow-hidden">
    {#each particles as p}
      <div
        class="absolute rounded-full bg-white opacity-70 animate-float"
        style="
          left: {p.x}%;
          top: {p.y}%;
          width: {p.size}px;
          height: {p.size}px;
          animation-delay: {p.delay}s;
          animation-duration: {p.duration}s;
        "
      ></div>
    {/each}
  </div>
  
  <style>
    @keyframes float {
      0% {
        transform: translateY(0) scale(1);
        opacity: 1;
      }
      100% {
        transform: translateY(-100vh) scale(0.5);
        opacity: 0;
      }
    }
    .animate-float {
      animation-name: float;
      animation-timing-function: ease-in;
      animation-iteration-count: infinite;
    }
  </style>