<script lang="ts">
	import { onMount } from "svelte";

    let numCircles = 4;
    let radiusStep = 60;
    let center = 300;
    const imgs = [ '/icons/react.svg','/icons/svelte.svg','/icons/nextjs.svg', '/icons/shopify.svg','/icons/figma.svg', '/icons/tailwind.svg', '/icons/git.svg','/icons/html.svg','/icons/css.svg','/icons/javascript.svg',];
    const iconsPerOrbit = [2, 3, 2, 3]
    const orbits: any = $state([]);
    let startingAngles= [
     0, Math.PI / 2, Math.PI / 3, Math.PI, Math.PI * 1.5
    ];
  
    function getPosition(radius: any, angle: any){
      return {
        x: center + radius * Math.cos(angle),
        y: center + radius * Math.sin(angle),
      };
    }
    let i = 0;
    let iconIndex = 0;
    for (i = 0; i < numCircles; i++)
    { 
        const r = (i + 1) * radiusStep;       
        let numIcons = iconsPerOrbit[i] ?? 1; 
        let startingAngle = startingAngles[i] ?? 1;
        const icons = [];

        for (let j = 0; j < numIcons; j++) {
            const angle = startingAngle + (Math.PI * 2 * j) / numIcons;
            icons.push({
            img: imgs[iconIndex++ % imgs.length],
            angle,
            speed:(i + 1) * 0.001, // slow rotation
        });
    }
    
        orbits.push({
            r,
            icons,
        });
    }
  // Animate the rotation
  function animate() {
    orbits.forEach((orbit: any) => {
      orbit.icons.forEach((icon:any) => {
        icon.angle += icon.speed;
      });
    });
    requestAnimationFrame(animate);
  }
  
  onMount(() => {
    animate();
  });
  </script>
  
  <svg width="600" height="600" viewBox="0 0 600 600">
    {#each orbits as orbit}
      <circle
        cx={center}
        cy={center}
        r={orbit.r}
        fill="none"
        stroke="oklch(44.2% 0.017 285.786)"
        stroke-width="1"
      />
    
        {#each orbit.icons as icon}
        {@const pos = getPosition(orbit.r, icon.angle)}
        <image
          href={icon.img}
          x={pos.x}
          y={pos.y}
          width="50"
          height="50"
          transform="translate(-25, -25)"
        />
        {/each}
    {/each}
  </svg>