<script>
  import Docs from './lib/Docs.svelte';
  import Navbar from './lib/components/Navbar.svelte';
  import HelloWorld from './lib/HelloWorld.svelte';
  import { Router, Route } from 'svelte-routing';
  export let url = '';
</script>

<main>
  <Navbar />
  <Router url={url}>
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
      <div class="grid grid-cols-3 mb-20">
        <img
                class="mx-auto my-auto max-h-60 max-w-60"
                alt="Sapling logo"
                src="https://saplingdata.com/wp-content/uploads/2021/04/powered-sapling-image-2.png">
        <img
                class="mx-auto my-auto max-h-60 max-w-60"
                alt="Svelte logo"
                src="https://upload.wikimedia.org/wikipedia/commons/1/1b/Svelte_Logo.svg">
        <img
                class="mx-auto my-auto max-h-60 max-w-60"
                alt="Vite logo"
                src="https://vitejs.dev/logo.svg">
      </div>
      <Route path="/">
        <HelloWorld />
      </Route>
      <Route path="docs">
        <Docs />
      </Route>
    </div>
  </Router>
</main>
