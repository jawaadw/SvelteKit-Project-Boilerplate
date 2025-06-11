<script lang="ts">
  import { goto } from "$app/navigation";
  import { page } from "$app/stores";
  import { MOBILE_WIDTH } from "$lib/Constants";
  import { Routes } from "../../utils/strings";
  import Button from "../components/Button.svelte";

  const { cleanup = () => {} } = $props();

  const pathname = $derived($page.url.pathname);

  let items: string[][] = [
    ["Home", "/"],
    ["About Us", "/about"],
    ["Services & Eligibility", "/services"],
    ["Appointments", "/appointments"],
    ["Gallery", "/gallery"],
    // [ "Blog", "/blog" ]
  ];
  let screenWidth = $state(Infinity);
</script>

<svelte:window bind:innerWidth={screenWidth} />

<nav class="max-lg:pt-xl 3xl:py-0 max-h-full flex flex-col">
  <ul class="flex-col lg:flex-row">
    {#each items as item, i}
      <a
        href={item[1]}
        onclick={cleanup}
        class="w-full lg:w-auto text-center text-lightgray lg:hover:text-lightgray hover:text-white hover:bg-lightgray lg:hover:bg-white hover:text-white rounded-lg py-sm"
      >
        <li aria-current={pathname === item[1] ? "page" : undefined}>
          {item[0]}
        </li>
      </a>
    {/each}
  </ul>

  {#if screenWidth < MOBILE_WIDTH}
    <div class="flex flex-col gap-4">
      <Button onClick={() => goto(Routes.volunteer)}>
        Join as a Volunteer
      </Button>
      <Button class="bg-orange" onClick={() => goto(Routes.donate)}>
        Donate
      </Button>
    </div>
  {/if}
</nav>

<style>
  nav {
    height: 100%;
  }

  ul {
    height: 100%;
    width: 100%;
    display: flex;
    gap: 20px;
    align-items: center;
  }

  li {
    list-style-type: none;
  }

  a > [aria-current="page"] {
    color: var(--darkblue);
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  a:has(> [aria-current="page"]) {
    background-color: white;
  }

  a > [aria-current="page"]::after {
    content: "";
    display: block;
    width: 50%;
    height: 2px;
    background-color: var(--orange);
  }

  a {
    text-decoration: none;
    text-wrap: nowrap;
  }
</style>

