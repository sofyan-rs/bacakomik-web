<script lang="ts">
  import { page } from '$app/stores';

  const menus = [
    { name: 'Home', href: '/', openInNewTab: false},
    { name: 'Report Bug', href: 'https://github.com/sofyan-rs/bacakomik-app-release/issues/new', openInNewTab: true},
    { name: 'Kebijakan Privacy', href: '/privacy-policy', openInNewTab: false},
    { name: 'DMCA', href: '/dmca', openInNewTab: false}
  ];

  let showMenu = false;

</script>

<header class="bg-blue-500/10 backdrop-blur-lg">
  <div class="container mx-auto flex flex-col md:flex-row">
    <div class="flex justify-between">
      <a href="/" class="flex items-center p-3 mr-5">
        <img class="w-10 h-10 rounded-md" src="/icon.png" alt="BacaKomik">
        <h1 class="text-2xl font-semibold ml-3 text-white">BacaKomik</h1>
      </a>
      <button on:click={() => showMenu = !showMenu} class="p-5 float-end md:hidden">
        {#if !showMenu}
          <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
          </svg>
        {:else}
          <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
          </svg>
        {/if}
      </button>
    </div>
    <nav class:show={showMenu}>
      {#each menus as menu}
        <a class:active="{$page.url.pathname === menu.href}" href={menu.href} target={menu.openInNewTab ? '_blank' : ''}>{menu.name}</a>
      {/each}
    </nav>
  </div>
</header>

<style lang="postcss">
  nav {
    @apply max-h-0 overflow-hidden transition-all ease-in-out duration-300 md:max-h-full;
  }
  nav.show {
    @apply max-h-96;
  }
  nav a {
    @apply p-5 inline-block w-full md:w-auto;
  }
  nav a:hover {
    @apply bg-blue-500/20 text-white;
  }
  nav a.active {
    @apply bg-blue-500/20 text-white;
  }
</style>