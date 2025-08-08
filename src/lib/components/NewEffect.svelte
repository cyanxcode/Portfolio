<div class="relative flex min-h-screen items-center justify-center overflow-hidden p-4">
	<h2
		class="karantina z-10 w-full text-center text-5xl font-extralight -tracking-normal text-white sm:text-7xl lg:text-8xl"
	>
		Creating Not Just Websites <br /> But a Story.
	</h2>

	<img
		src="/img/me2.jpg"
		alt="A professional headshot"
		class="animate-float absolute top-[70%] left-[10%] h-20 w-20 rounded-full object-cover sm:top-[65%] sm:right-[20%] md:h-28 md:w-28"
		style="animation-delay: 0s;"
	/>

	<img
		src="/img/profile.jpeg"
		alt="A professional headshot"
		class="animate-float absolute top-[25%] right-[10%] h-16 w-16 rounded-full object-cover sm:top-[30%] sm:right-[15%] md:h-20 md:w-20"
		style="animation-delay: 1.5s;"
	/>

	<img
		src="/img/me.jpg"
		alt=""
		class="animate-float absolute top-[15%] left-[30%] h-16 w-16 rounded-full object-cover sm:top-[20%] sm:left-[50%] md:h-24 md:w-24 lg:left-[60%]"
		style="animation-delay: 3s;"
	/>
</div>

<style>
	/* Keyframe animation for the floating effect */
	@keyframes float {
		0% {
			transform: translateY(0px);
		}
		50% {
			transform: translateY(-15px);
		}
		100% {
			transform: translateY(0px);
		}
	}

	/* Applying the animation */
	.animate-float {
		animation: float 6s ease-in-out infinite;
	}
</style>
