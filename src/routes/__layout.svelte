<script context="module" lang="ts">
  import type { ErrorLoad } from '@sveltejs/kit'

  const modules = import.meta.glob('/src/routes/**/!(_*).svelte')
  
  const routes = Object.keys(modules).map((key) => {
    const path = key.split('/src/routes').join('').replace(/(.svelte|index)/g, '')
    const name = path.substring(path.indexOf('/') + 1) || 'index'
    return {
      name,
      path,
    }
  })

  export const load: ErrorLoad = async ({ fetch }) => {
    return {
      status: 200,
      props: {
        routes,
      }
    }
  }
</script>

<script>
  import '../app.css'
  import { page } from '$app/stores'
  
  export let routes = []

  let menu = routes
  .sort((a, b) => a.name === 'index' ? -1 : b.name === 'index' ? 1 : 0)
  .map(route => {
    return {
      name: route.name
        .replace(/^\w/, c => c.toUpperCase())
        .replace(/\/index/, '')
      ,
      path: route.path,
    }
  })
</script>

<svelte:head>
  <link rel="stylesheet" href="/css/main.css" />
</svelte:head>

<header class="fixed w-full h-auto bg-white z-50">
  <nav class="flex items-center">
    <ul class="flex space-x-6 justify-center p-4">
      {#each menu as { name, path }}
        <li>
          <a class:line-through={$page.url.pathname === path} href={path}>{name}</a>
        </li>
      {/each}
    </ul>
    <a href="https://github.com/jancassio/mouse-coordinates-with-css-vars">Source</a>
  </nav>
</header>

<slot />
