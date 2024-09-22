<script lang="ts">
  import * as Card from "$lib/components/ui/card/index.js";
  import * as Carousel from "$lib/components/ui/carousel/index.js";
  import Dialog from "$lib/components/ui/dialog/Dialog.svelte";
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
  <div class=" w-11/12 cursor-pointer h-fit">
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
        class="image-grid-col-2 image-grid-row-2 rounded-l-2xl"
        src="../../1.jpeg"
        alt="clock"
      />
      <img src="../../2.jpeg" alt="architecture" />
      <img src="../../3.jpeg" alt="architecture" class="rounded-tr-2xl" />
      <img src="../../4.jpeg" alt="architecture" />
      <img src="../../5.jpeg" alt="architecture" class="rounded-br-2xl" />
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
</div>

<style>
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
