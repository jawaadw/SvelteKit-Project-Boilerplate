<script lang="ts">
  import { page } from "$app/state";
  import { MOBILE_WIDTH } from "$lib/Constants";
  import { Routes } from "../../utils/strings";

  const { columnBreak = true, cleanup = () => {} } = $props();

  const pathname = $derived(page.url.pathname);

  const routeKeys = Object.keys(Routes);

  let screenWidth = $state(Infinity);
</script>

<svelte:window bind:innerWidth={screenWidth} />

<nav class="max-h-full h-full flex">
  <ul
    class="size-full flex sm:gap-[48px] items-center {columnBreak
      ? 'max-sm:flex-col max-sm:mt-12'
      : 'max-sm:gap-[10px]'} flex-row"
  >
    {#each routeKeys as item, i}
      <a
        href={Routes[item]}
        onclick={() => cleanup()}
        class="group w-full text-center no-underline py-4 {columnBreak
          ? 'max-sm:hover:bg-primary'
          : ''}"
      >
        <li
          aria-current={pathname === Routes[item] ? "page" : undefined}
          class="list-none aria-[current=page]:text-secondary aria-[current=page]:underline text-white group-hover:text-secondary {columnBreak
            ? 'max-sm:text-black max-sm:group-hover:text-white'
            : ''}"
        >
          {item}
        </li>
      </a>

      {#if screenWidth < MOBILE_WIDTH && i < routeKeys.length - 1}
        <hr class="border-neutral w-3/5" />
      {/if}
    {/each}
  </ul>
</nav>
