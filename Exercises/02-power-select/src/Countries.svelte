<script>
  import { createEventDispatcher } from "svelte";

  export let id;
  export let src;
  export let name;

  const dispatch = createEventDispatcher();
</script>

<li class="relative">
  <div
    class="block w-full overflow-hidden bg-gray-100 rounded-lg group aspect-w-10 aspect-h-7 focus-within:ring-2 focus-within:ring-offset-2 focus-within:ring-offset-gray-100 focus-within:ring-indigo-500"
  >
    <img
      {src}
      alt="flag"
      class="object-cover pointer-events-none group-hover:opacity-75"
    />
  </div>
  <p
    class="block mt-2 text-sm font-medium text-gray-900 truncate pointer-events-none"
  >
    {name}
  </p>
</li>
