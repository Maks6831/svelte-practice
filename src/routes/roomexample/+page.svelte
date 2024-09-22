<script lang="ts">
  import * as Card from "$lib/components/ui/card/index.js";
  import * as Carousel from "$lib/components/ui/carousel/index.js";
  import Dialog from "$lib/components/ui/dialog/Dialog.svelte";
  import CalendarIcon from "svelte-radix/Calendar.svelte";
  import type { DateRange } from "bits-ui";
  import {
    today,
    CalendarDate,
    DateFormatter,
    type DateValue,
    getLocalTimeZone,
  } from "@internationalized/date";
  import { cn } from "$lib/utils.js";
  import { Button } from "$lib/components/ui/button/index.js";
  import { RangeCalendar } from "$lib/components/ui/range-calendar/index.js";
  import * as Popover from "$lib/components/ui/popover/index.js";

  const df = new DateFormatter("en-US", {
    dateStyle: "medium",
  });

  let value: DateRange | undefined = {
    start: today("America/New_york").add({ days: 10 }),
    end: today("America/New_york").add({ days: 20 }),
  };

  let startValue: DateValue | undefined = undefined;
  let dialog: {
    showModal(): any;
    close(): any;
  };
  const imageArray = [
    "../../1.jpeg",
    "../../2.jpeg",
    "../../3.jpeg",
    "../../4.jpeg",
    "../../5.jpeg",
    "../../6.jpeg",
    "../../7.jpeg",
    "../../8.jpeg",
    "../../9.jpeg",
    "../../10.jpeg",
    "../../11.jpeg",
    "../../12.jpeg",
    "../../13.jpeg",
    "../../14.jpeg",
    "../../15.jpeg",
    "../../16.jpeg",
    "../../17.jpeg",
    "../../18.jpeg",
  ];

  $: index = 0;
  const changeImage = (i: number) => {
    index = i;
  };
</script>

<div class="w-full min-h-screen flex flex-col justify-start items-center">
  <div class=" flex flex-col-reverse lg:flex-col w-11/12 cursor-pointer h-fit">
    <div class="w-full flex justify-between pt-4 px-4">
      <h3 class=" font-semibold text-3xl">Wake up in the Musee d'Orsay</h3>
      <div class="flex gap-4">
        <div class="p-3 flex gap-2">
          <div class="">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              class="size-5"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M3 16.5v2.25A2.25 2.25 0 0 0 5.25 21h13.5A2.25 2.25 0 0 0 21 18.75V16.5m-13.5-9L12 3m0 0 4.5 4.5M12 3v13.5"
              />
            </svg>
          </div>
          <div class="underline text-gray-500 text-sm">Share</div>
        </div>
        <div class="p-3 flex gap-2">
          <div class="">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              class="size-5"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M21 8.25c0-2.485-2.099-4.5-4.688-4.5-1.935 0-3.597 1.126-4.312 2.733-.715-1.607-2.377-2.733-4.313-2.733C5.1 3.75 3 5.765 3 8.25c0 7.22 9 12 9 12s9-4.78 9-12Z"
              />
            </svg>
          </div>
          <div class="underline text-gray-500 text-sm">save</div>
        </div>
      </div>
    </div>
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div class="image-grid" on:click={() => dialog.showModal()}>
      <img
        class="image-grid-col-2 image-grid-row-2 rounded-r-2xl lg:rounded-r-none rounded-l-2xl"
        src="../../1.jpeg"
        alt="clock"
      />
      <img class="hidden lg:block" src="../../2.jpeg" alt="architecture" />
      <img
        class="hidden lg:block rounded-tr-2xl"
        src="../../3.jpeg"
        alt="architecture"
      />
      <img class="hidden lg:block" src="../../4.jpeg" alt="architecture" />
      <img
        class="hidden lg:block rounded-br-2xl"
        src="../../5.jpeg"
        alt="architecture"
      />
    </div>
  </div>
  <Dialog bind:dialog>
    <div
      class="w-screen h-screen bg-white relative rounded-2xl border-none flex justify-center items-center"
    >
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <!-- svelte-ignore a11y-no-static-element-interactions -->
      <div
        class="absolute top-5 left-5 cursor-pointer"
        on:click={() => dialog.close()}
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="size-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M10.5 19.5 3 12m0 0 7.5-7.5M3 12h18"
          />
        </svg>
      </div>
      <div class="gallery">
        {#each imageArray as image}
          <div class="p-2 gallery-item">
            <img src={image} alt="rooms" />
          </div>
        {/each}
      </div>
    </div>
  </Dialog>
  <div class=" flex justify-between pt-2 px-4 w-11/12">
    <div class="flex flex-col gap-y-2 w-1/2">
      <div class="text-2xl font-medium">Paris, France</div>
      <div>2 guests &#183; 1 bedroom &#183; 1 bathroom</div>
      <div class="flex justify-start items-center">
        <div class="pr-2">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            fill="currentColor"
            class="size-3"
          >
            <path
              fill-rule="evenodd"
              d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z"
              clip-rule="evenodd"
            />
          </svg>
        </div>
        <div>5.0 &#183 <span class="underline">1 review</span></div>
      </div>
    </div>
    <div
      class="w-1/3 h-64 boxshadow-1 rounded-2xl flex flex-col justify-start gap-2 items-center p-4"
    >
      <div>Choose dates</div>
      <div class="grid gap-2">
        <Popover.Root openFocus>
          <Popover.Trigger asChild let:builder>
            <Button
              variant="outline"
              class={cn(
                "w-[300px] justify-start text-left font-normal",
                !value && "text-muted-foreground"
              )}
              builders={[builder]}
            >
              <CalendarIcon class="mr-2 h-4 w-4" />
              {#if value && value.start}
                {#if value.end}
                  {df.format(value.start.toDate(getLocalTimeZone()))} - {df.format(
                    value.end.toDate(getLocalTimeZone())
                  )}
                {:else}
                  {df.format(value.start.toDate(getLocalTimeZone()))}
                {/if}
              {:else if startValue}
                {df.format(startValue.toDate(getLocalTimeZone()))}
              {:else}
                Pick a date
              {/if}
            </Button>
          </Popover.Trigger>
          <Popover.Content class="w-auto p-0" align="start">
            <RangeCalendar
              bind:value
              bind:startValue
              placeholder={value?.start}
              initialFocus
              numberOfMonths={2}
            />
          </Popover.Content>
        </Popover.Root>
      </div>
    </div>
  </div>
</div>

<style>
  .boxshadow-1 {
    box-shadow:
      rgba(0, 0, 0, 0.05) 0px 6px 24px 0px,
      rgba(0, 0, 0, 0.08) 0px 0px 0px 1px;
  }
  .image-grid {
    --gap: 16px;
    --num-cols: 4;
    --row-height: 200px;

    box-sizing: border-box;
    padding: var(--gap);

    display: grid;
    grid-template-columns: repeat(var(--num-cols), 1fr);
    grid-auto-rows: var(--row-height);
    gap: var(--gap);
  }

  .image-grid > img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .image-grid-col-2 {
    grid-column: span 2;
  }

  .image-grid-row-2 {
    grid-row: span 2;
  }

  /* Anything udner 1024px */
  @media screen and (max-width: 1024px) {
    .image-grid {
      --num-cols: 2;
      --row-height: 200px;
    }
  }

  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 10px;
  }

  .gallery-item img {
    width: 100%;
    height: auto;
    border-radius: 8px;
  }
</style>
