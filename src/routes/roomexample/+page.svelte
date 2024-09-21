<script lang="ts">
  import * as Card from "$lib/components/ui/card/index.js";
  import * as Carousel from "$lib/components/ui/carousel/index.js";
  const imageArray = [
    "image-1.png",
    "image-2.png",
    "image-3.png",
    "image-4.png",
    "image-5.png",
  ];
</script>

<div class="w-full min-h-screen flex flex-col justify-start items-center">
  <div class="shadow-lg w-11/12 h-72">
    <div class=" w-full md:w-1/2">
      <Carousel.Root class="w-full max-w-xs">
        <Carousel.Content>
          {#each imageArray as image}
            <Carousel.Item>
              <div class="p-1">
                <Card.Root>
                  <Card.Content
                    class="flex aspect-square items-center justify-center p-6"
                  >
                    <img src="../../{image}" />
                  </Card.Content>
                </Card.Root>
              </div>
            </Carousel.Item>
          {/each}
        </Carousel.Content>
        <Carousel.Previous />
        <Carousel.Next />
      </Carousel.Root>
    </div>
  </div>
</div>
