<script lang="ts">
	let mouseX = 0
	let mouseY = 0
	let ratioX = 0
	let ratioY = 0
	let mouseDistanceX = 0
	let mouseDistanceY = 0
	let oldX = 0
	let oldY = 0
	let steps = 0

	// function onMouseMove(event: EventParam<MouseEvent, HTMLElement>) {
	const onMouseMove: svelte.JSX.MouseEventHandler<Window> = (event) => {
		mouseX = event.clientX
		mouseY = event.clientY
		steps = Math.abs(oldX - mouseX + (oldY - mouseY))
		requestAnimationFrame(update)
	}

	function update(time: number) {
		if (steps === 0) return

		mouseDistanceX = mouseX / window.innerWidth
		mouseDistanceY = mouseY / window.innerHeight
		ratioX = -1 + mouseX / (window.innerWidth * 0.5)
		ratioY = -1 + mouseY / (window.innerHeight * 0.5)

		document.documentElement.style.setProperty('--mouse-x', `${mouseX}`)
		document.documentElement.style.setProperty('--mouse-y', `${mouseY}`)
		document.documentElement.style.setProperty('--mouse-dx', mouseDistanceX.toFixed(2))
		document.documentElement.style.setProperty('--mouse-dy', mouseDistanceY.toFixed(2))
		document.documentElement.style.setProperty('--mouse-rx', ratioX.toFixed(2))
		document.documentElement.style.setProperty('--mouse-ry', ratioY.toFixed(2))

		oldX = mouseX
		oldY = mouseY
		steps -= 1
		requestAnimationFrame(update)
	}
</script>

<svelte:window on:mousemove={onMouseMove} />

<style>
  :root {
    --mouse-x: 0;
    --mouse-y: 0;
    --mouse-dx: 0;
    --mouse-dy: 0;
    --mouse-rx: 0;
    --mouse-ry: 0;
  }
</style>