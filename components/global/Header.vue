<template>
  <nav class="bg-white">
    <div class="flex items-center justify-center">
      <div class="absolute top-5 left-0 sm:hidden">
        <!-- Mobile menu button-->
        <button
          @click="open = !open"
          type="button"
          class="inline-flex items-center justify-center p-2 rounded-md hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
          aria-controls="mobile-menu"
          aria-expanded="false"
        >
          <span class="sr-only">Open main menu</span>
          <svg
            class="block h-6 w-6"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            aria-hidden="true"
          >
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
          </svg>
          <svg
            class="hidden h-6 w-6"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            aria-hidden="true"
          >
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>
      <div class="flex items-center justify-center">
        <div class="flex align-center items-center m-2">
          <nuxt-link :to="localePath('/')" class="flex items-center">
            <img class="block lg:hidden h-24" src="/icon.png" alt="Workflow" />
            <img class="hidden lg:block h-24" src="/icon.png" alt="Workflow" />
            <span class="hidden lg:block ml-2 font-black uppercase">Weinmacher Nick</span>
          </nuxt-link>
        </div>
        <div class="hidden sm:block sm:ml-6">
          <div class="flex space-x-4">
            <nuxt-link
              @click="open = false"
              class="hover:bg-gray-700 px-3 py-2 rounded-md text-sm font-medium"
              v-for="route of routes"
              :key="route.name"
              :to="localePath(route.route)"
              >{{ route.name }}</nuxt-link
            >
          </div>
        </div>
      </div>
    </div>

    <div v-if="open" class="sm:hidden" id="mobile-menu">
      <div class="px-2 pt-2 pb-3 space-y-1">
        <nuxt-link
          @click="open = false"
          class="hover:bg-gray-700 block px-3 py-2 rounded-md text-base font-medium"
          v-for="route of routes"
          :key="route.name"
          :to="localePath(route.route)"
          >{{ route.name }}</nuxt-link
        >
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Header',
  data: () => {
    return {
      open: false,
      routes: [
        { name: 'Über uns', route: '/about' },
        { name: 'Rebsorten', route: '/projects' },
        { name: 'News', route: '/blog' },
        { name: 'Kontakt', route: '/contact' }
      ]
    };
  }
};
</script>

<style lang="postcss" scoped></style>
