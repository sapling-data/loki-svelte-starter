<script>
import { onMount } from 'svelte';
import {
  Disclosure,
  DisclosureButton,
  DisclosurePanel,
  Transition,
  Menu,
  MenuButton,
  MenuItems,
  MenuItem,
} from '@rgossiaux/svelte-headlessui';
import { Link, Router } from 'svelte-routing';
import CloudMenu from './CloudMenu.svelte';
import { Icon } from '@steeze-ui/svelte-icon';
import { X } from '@steeze-ui/heroicons'
import { Menu as MenuIcon } from '@steeze-ui/heroicons'
import { Cog } from '@steeze-ui/heroicons'
export let navigation = [];
export let basepath = '';

const logout = async () => {
  await loki.user.logout();
  document.location.reload();
};
</script>

<Disclosure as="nav" class="bg-gray-800" let:open>
  <div class="px-2 mx-auto sm:px-6 lg:px-8">
      <div class="relative flex items-center justify-between h-16">
        <div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
          <DisclosureButton class="inline-flex items-center justify-center p-2 text-gray-400 rounded-md hover:text-white hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white">
            <span class="sr-only">Open main menu</span>
            {#if open}
              <Icon src={X} theme="outline" class="block w-6 h-6" aria-hidden="true" />
            {:else}
              <Icon src={MenuIcon} theme="outline" class="block w-6 h-6" aria-hidden="true" />
            {/if}
          </DisclosureButton>
        </div>
        <div class="flex items-center justify-center flex-1 sm:items-stretch sm:justify-start">
          <CloudMenu />
          <div class="flex-shrink-0 flex items-center">
            <img class="block lg:hidden h-10 w-auto" src="https://saplingdata.com/wp-content/themes/sapling/img/sapling-data-logo.svg" alt="Sapling Data" />
            <img class="hidden lg:block h-10 w-auto" src="https://saplingdata.com/wp-content/themes/sapling/img/sapling-data-logo.svg" alt="Sapling Data" />
          </div>
          <div class="hidden sm:block sm:ml-6">
            <div class="flex items-center space-x-4">
              <Router>
                {#each navigation as item}
                  <Link
                          to={basepath + item.to}
                          class="text-white px-3 py-2 rounded-md text-sm font-medium"
                  >
                    {item.name}
                  </Link>
                {/each}
              </Router>
            </div>
          </div>
        </div>
        <div class="absolute inset-y-0 right-0 z-50 flex items-center pr-2 sm:static sm:inset-auto sm:ml-6 sm:pr-0">
          <Menu as="div" class="relative ml-3">
            <div>
              <MenuButton
                  class="flex text-sm text-gray-400 bg-gray-800 rounded-full hover:text-white focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white">
                <span class="sr-only">Open user menu</span>
                <Icon src={Cog} theme="outline" class="h-6 w-6" aria-hidden="true" />
              </MenuButton>
            </div>
            <Transition enter="transition ease-out duration-100"
                        enterFrom="transform opacity-0 scale-95"
                        enterTo="transform opacity-100 scale-100"
                        leave="transition ease-in duration-75"
                        leaveFrom="transform opacity-100 scale-100"
                        leaveTo="transform opacity-0 scale-95">
              <MenuItems
                      class="origin-top-right absolute right-0 mt-2 w-48
              rounded-md shadow-lg py-1 bg-white ring-1 ring-black
              ring-opacity-5 focus:outline-none">
                <MenuItem>
                  <button class="block px-4 py-2 text-sm text-gray-700 w-full text-left" on:click={logout}>Log out</button>
                </MenuItem>
              </MenuItems>
            </Transition>
          </Menu>
        </div>
      </div>
    </div>

    <DisclosurePanel class="sm:hidden">
      <div class="px-2 pt-2 pb-3 space-y-1">
        {#each navigation as item}
          <Link
              to={basepath + item.to}
              class="text-gray-300 hover:bg-gray-700 hover:text-white block px-3 py-2 rounded-md text-base font-medium"
          >
            {item.name}
          </Link>
        {/each}
      </div>
    </DisclosurePanel>
</Disclosure>
