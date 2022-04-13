<script>
	import MouseEventsTracker from '$lib/components/MouseEventsTracker.svelte'
</script>

<section class="w-full h-full grid place-items-center overflow-hidden">
  <h1 class="floating-title title text-9xl uppercase font-black">HELLO WORLD</h1>
</section>

<MouseEventsTracker />

<style>
  .floating-title {
		transform: perspective(700px) rotate3d(0, 0, 0, 0deg) translate3d(15px, 30px, 0);
	}

  @media (hover: hover) {
		.floating-title {
			--x: calc(15px + (-15% * var(--mouse-rx)));
			--y: calc(30px + (-30% * var(--mouse-ry)));
			--rx: calc(-1 * var(--mouse-ry));
			--ry: var(--mouse-rx);
			--deg: 22deg;
			--perspective: 700px;
			--easeOutQuad: cubic-bezier(0.5, 1, 0.89, 1);

			transform: perspective(var(--perspective)) rotate3d(var(--rx), var(--ry), 0, var(--deg))
				translate3d(var(--x), var(--y), 0);
		}
	}

  .title {
		color: rgb(255, 0, 0);
	}

</style>