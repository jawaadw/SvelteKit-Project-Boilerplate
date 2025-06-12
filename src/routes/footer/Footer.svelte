<script lang="ts">
  import Button from "$lib/components/ui/button/button.svelte";
  import { Facebook, Linkedin } from "@lucide/svelte";
  import NavItems from "../header/NavItems.svelte";

  const iconButtonClass =
    "bg-white text-primary p-1 size-8 rounded-md border hover:bg-primary hover:text-white hover:border-white";
  const iconClass = "size-6 fill-current";
</script>

<div
  class="footer w-full flex flex-col gap-lg items-center bg-primary pb-4 text-sm"
>
  <div class="w-full flex justify-between items-center px-8">
    <a href="/">
      <img class="w-[150px]" src="./images/Logo-Text.png" alt="Logo" />
    </a>

    <NavItems columnBreak={false}></NavItems>

    <div class="flex gap-2">
      <Button class={iconButtonClass}>
        <Facebook class={iconClass} strokeWidth="0.5" />
      </Button>
      <Button class={iconButtonClass}>
        <Linkedin class={iconClass} strokeWidth="0.5" />
      </Button>
    </div>
  </div>

  <p class="text-neutral">Hope Tech © 2025 <br /> All rights reserved.</p>
</div>

