<section class="w-full h-full grid place-items-center p-8">
  <article>
    <h1 class="text-4xl uppercase">Mouse Coordinates with CSS vars</h1>
    <hr>
    <div class="py-4 text-lg flex flex-col leading-relaxed">
      <p>
        This demo shows how to use CSS variables to access mouse coordinates.
      </p>
      
      <p>
        First and most important, mouse coordinates are not available in CSS yet, the values are provided by script.
        So keep in mind to have a non script support fallback.
      </p>
      
      <p>
        For mobile devices, mouse move events are not supported yet, so you can't use this demo on mobile devices.
        However, touch events are converted to mouse clicks, so mouse clicks will provide coordinates on the touch of screen.
      </p>
      <p>
        Finally, the implementation is made with Svelte, but it could be easily converted to vanilla JS.
      </p>
    </div>
  </article>
</section>