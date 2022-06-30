<script>
  import lokiConfig from '../loki.config';
  import Docs from './lib/Docs.svelte';
  import Navbar from './lib/components/Navbar.svelte';
  import HelloWorld from './lib/HelloWorld.svelte';
  import { Router, Route, navigate } from 'svelte-routing';
  import { onMount } from 'svelte';
  export const navigation = [
    {
      name: 'Hello World',
      to: '/',
      component: HelloWorld,
    },
    {
      name: 'Docs',
      to: '/docs',
      component: Docs,
    },
  ]
  export let basepath = import.meta.env.MODE === 'development'
    ? `/${lokiConfig.appName}/pages/urn/com/${lokiConfig.cloudName}/${lokiConfig.appModelName}/app/pages/${lokiConfig.pageName}/v`
    : `/${loki.urn.getLastSegment(loki.app.appInstanceUrn)}/pages/urn/com/${lokiConfig.appRoot}/${lokiConfig.appModelName}/app/pages/${lokiConfig.pageName}/v`;

  if (import.meta.env.MODE === 'development') onMount(() => navigate(basepath + '/', { replace: true }))
</script>

<Router>
  <main>
    <Navbar navigation={navigation} basepath={basepath} />
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
      {#each navigation as item }
        <Route path={basepath + item.to} component={item.component} />
      {/each}
    </div>
  </main>
</Router>
