<script lang="ts">
  import { type LoadStatus } from "$lib/types";
  import { Image } from "@unpic/svelte";
  import { getContext } from "svelte";
  import { fade } from "svelte/transition";

  let loadStatus = getContext<LoadStatus>("loadStatus");
</script>

<div
  class="fixed w-full h-full z-50 top-0 flex justify-center items-center bg-mocha-base"
  out:fade={{ duration: 500 }}
  onintrostart={() => {
    loadStatus.transitioning = true;
    console.log("Splash intro start");
  }}
  onoutroend={() => {
    loadStatus.transitioning = false;
    console.log("Splash intro end");
  }}
>
  <Image
    src="/favicon.png"
    layout="fixed"
    width={96}
    height={96}
    alt=""
    class="rounded-full animate-pulse"
  />
</div>
