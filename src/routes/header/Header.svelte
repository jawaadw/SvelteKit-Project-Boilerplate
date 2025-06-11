<script lang="ts">
    import { Menu } from "lucide-svelte";
    import Button from "../components/Button.svelte";
    import NavItems from "./NavItems.svelte";
    import * as Sheet from "$lib/components/ui/sheet";
    import { beforeNavigate, goto } from "$app/navigation";
    import { Routes } from "../../utils/strings";
    import { MOBILE_WIDTH } from "$lib/Constants";
    import { tick } from "svelte";

    let sheetOpen = $state(false);
    let screenWidth = $state(Infinity);

    function closeSheet() {
      sheetOpen = false;
    }

    async function navigate(route: string) {
      closeSheet();
      await tick();
      goto(route);
    }

    beforeNavigate(() => { closeSheet(); })
</script>

<svelte:window bind:innerWidth={screenWidth}></svelte:window>

<header class="flex h-[100px] p-sm px-[64px] max-[1150px]:p-sm gap-[10px] items-center justify-between">
  <a style:height="100%" href="/">
    <img class="h-full pr-lg"
         src="./images/Logo-Color-Light.png"
         alt="Carolina Q&A Logo">
  </a>

  <div class="grow"></div>

  <div class="flex h-full items-center hidden lg:flex">
    <NavItems></NavItems>
    <div class="bg-lightgray opacity-50 w-[1px] h-1/4 mx-md"></div>
  </div>

  <div class="flex gap-md items-center">
    {#if screenWidth > MOBILE_WIDTH}
      <Button onClick={() => navigate(Routes.volunteer) }>
        Join as a Volunteer
      </Button>
      <Button class="bg-orange" onClick={() => navigate(Routes.donate) }>
        Donate
      </Button>
    {/if}
    <Sheet.Root bind:open={sheetOpen}>
      <Sheet.Trigger asChild let:builder>
        <Button class="bg-transparent text-black hover:bg-darkgray hover:text-white border border-black rounded-lg px-2 flex lg:hidden"
                builders={[builder]}
                variant="outline">
          <Menu class="block lg:hidden w-[28px] h-auto" />
        </Button>
      </Sheet.Trigger>
      <Sheet.Content side="right">
        <NavItems cleanup={closeSheet}></NavItems>
      </Sheet.Content>
    </Sheet.Root>
  </div>
</header>