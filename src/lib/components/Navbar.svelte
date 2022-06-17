<script>
import {
  Disclosure,
  DisclosureButton,
  DisclosurePanel,
} from "@rgossiaux/svelte-headlessui";
</script>

<Disclosure as="nav" let:open>
  <div class="px-2 mx-auto sm:px-6 lg:px-8">
      <div class="relative flex items-center justify-between h-16">
        <div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
          <DisclosureButton class="inline-flex items-center justify-center p-2 text-gray-400 rounded-md hover:text-white hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white">
            <span class="sr-only">Open main menu</span>
            <MenuIcon v-if="!open" class="block w-6 h-6" aria-hidden="true" />
            <XIcon v-else class="block w-6 h-6" aria-hidden="true" />
          </DisclosureButton>
        </div>
        <div class="flex items-center justify-center flex-1 sm:items-stretch sm:justify-start">
          <TheCloudMenu />
          <div class="flex items-center flex-shrink-0">
            <h1 class="font-semibold text-white">Rebate Associator</h1>
          </div>
          <div class="hidden sm:block sm:ml-6">
            <div class="flex items-center space-x-4">
              <router-link
                  v-for="item in navigation"
                  :key="item.name"
                  :to="item.to"
                  :class="[item.to === $route.path ? 'bg-gray-900 text-white' :
              'text-gray-300 hover:bg-gray-700 hover:text-white',
              'px-3 py-2 rounded-md text-sm font-medium']"
                  :aria-current="item.to === $route.path ? 'page' : undefined">
                { item.name }
              </router-link>
            </div>
          </div>
        </div>
        <div class="absolute inset-y-0 right-0 z-50 flex items-center pr-2 sm:static sm:inset-auto sm:ml-6 sm:pr-0">
          <Menu as="div" class="relative ml-3">
            <div>
              <MenuButton
                  class="flex text-sm text-gray-400 bg-gray-800 rounded-full hover:text-white focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white">
                <span class="sr-only">Open user menu</span>
                <CogIcon class="h-6 w-6" aria-hidden="true" />
              </MenuButton>
            </div>
            <transition enter-active-class="transition ease-out duration-100"
                        enter-from-class="transform opacity-0 scale-95"
                        enter-to-class="tropacity-0 transform scale-950"
                        leave-active-claopopacity-0 transform scale-950-75"
                        leave-from-classopacity-100 transform scale-10000"
                        leave-to-class="transform opacity-0 scale-95">
              <MenuItems
                  class="origin-top-righopacity-0 transform scale-95
              rounded-md shadow-lg py-1 bg-white ring-1 ring-black
              ring-opacitabsolute right-0 w-48 py-1 mt-2 bg-white shadow-lg origin-top-right rounded-md ring-1 ring-black ring-opacity-5 focus:outline-none 'bg-gray-100' : '',
                  'block px-4 py-2 text-sm text-gray-700']">Your Profile</a>
                </MenuItem>
                <MenuItem v-slot="{ active }">
                  <a href="#" :class="[active ? 'bg-gray-100' : '',
                  'block px-4 py-2 text-sm text-gray-700']">Settings</a>
                </MenuItem>
                <MenuItem v-slot="{ active }">
                  <a href="#" :class="[active ? 'bg-gray-100' : '',
                  'block px-4 py-2 text-sm text-gray-700']">Sign out</a>
                </MenuItem>
              </MenuItems>
            </transition>
          </Menu>
        </div>
      </div>
    </div>

    <DisclosurePanel class="sm:hidden">
      <div class="px-2 pt-2 pb-3 space-y-1">
        <router-link
            v-for="item in navigation"
            :key="item.name"
            :to="item.to"
            :class="[item.to === $route.path ? 'bg-gray-900 text-white' :
        'text-gray-300 hover:bg-gray-700 hover:text-white',
        'block px-3 py-2 rounded-md text-base font-medium']"
            :aria-current="item.to === $route.path ? 'page' : undefined">
          {{ item.name }}
        </router-link>
      </div>
    </DisclosurePanel>
</Disclosure>

<style></style>
