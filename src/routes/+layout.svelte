<script>
  import "../app.css";
</script>

<div
  class="w-full flex flex-col justify-center items-center border-red-600 border"
>
  <nav class="">
    <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
      <div class="relative flex h-16 items-center justify-between">
        <div
          class="flex flex-1 items-center justify-center sm:items-stretch sm:justify-start"
        >
          <div class="flex flex-shrink-0 items-center">
            <img
              class="h-8 w-auto"
              src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=500"
              alt="Your Company"
            />
          </div>
          <div class="hidden sm:ml-6 sm:block">
            <div class="flex space-x-4">
              <a
                href="/"
                class="rounded-md bg-gray-900 px-3 py-2 text-sm font-medium text-white"
                aria-current="page">Home</a
              >
              <a
                href="/project"
                class="rounded-md px-3 py-2 text-sm font-medium text-black hover:bg-gray-700 hover:text-white"
                >Project</a
              >
              <a
                href="/gallery"
                class="rounded-md px-3 py-2 text-sm font-medium text-black hover:bg-gray-700 hover:text-white"
                >Gallery</a
              >
              <a
                href="/visit"
                class="rounded-md px-3 py-2 text-sm font-medium text-black hover:bg-gray-700 hover:text-white"
                >Visit</a
              >
              <a
                href="/roomexample"
                class="rounded-md px-3 py-2 text-sm font-medium text-black hover:bg-gray-700 hover:text-white"
                >booking</a
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>

  <slot></slot>
</div>
