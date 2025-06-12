<script lang="ts">
  import { Menu } from "@lucide/svelte";
  import NavItems from "./NavItems.svelte";
  import { buttonVariants } from "$lib/components/ui/button";
  import * as Sheet from "$lib/components/ui/sheet";
  import { beforeNavigate } from "$app/navigation";
  import { MOBILE_WIDTH } from "$lib/Constants";

  let sheetOpen = $state(false);
  let screenWidth = $state(Infinity);

  function closeSheet() {
    sheetOpen = false;
  }

  beforeNavigate(() => {
    closeSheet();
  });
</script>

<svelte:window bind:innerWidth={screenWidth} />

<header
  class="flex h-[86px] p-[12px] bg-primary rounded-xl max-[1150px]:p-sm gap-[10px] items-center justify-between"
>
  <a style:height="100%" href="/">
    <img
      class="h-full pr-lg"
      src="./images/Logo-Mark.png"
      alt="Carolina Q&A Logo"
    />
  </a>

  <div class="grow"></div>

  <div class="flex h-full items-center max-sm:hidden">
    <NavItems></NavItems>
  </div>

  <div class="flex gap-md items-center">
    {#if screenWidth < MOBILE_WIDTH}
      <Sheet.Root bind:open={sheetOpen}>
        <Sheet.Trigger
          class="border border-primary hover:text-secondary hover:border-secondary {buttonVariants(
            {
              variant: 'default',
            },
          )}"
        >
          <Menu class="block lg:hidden size-6 h-auto" />
        </Sheet.Trigger>
        <Sheet.Content side="right">
          <NavItems cleanup={closeSheet}></NavItems>
        </Sheet.Content>
      </Sheet.Root>
    {/if}
  </div>
</header>

