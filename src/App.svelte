<script>
  import logo from './assets/svelte.png';
  import Counter from './lib/Counter.svelte';
  import Navbar from './lib/components/Navbar.svelte';
</script>

<main>
  <Navbar />
  <img src={logo} alt="Svelte Logo" />
  <h1>Hello world!</h1>

  <Counter />

  <p>
    Visit <a href="https://svelte.dev">svelte.dev</a> to learn how to build Svelte
    apps.
  </p>

  <button class="px-4 py-2 text-white bg-blue-500 rounded-md hover:bg-blue-400">HELLO</button>

  <p>
    Check out <a href="https://github.com/sveltejs/kit#readme">SvelteKit</a> for
    the officially supported framework, also powered by Vite!
  </p>
</main>

<style>
</style>
