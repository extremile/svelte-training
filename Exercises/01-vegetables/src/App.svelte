<script>
  import "./assets/css/style.css";
  import Vegetables from "./Vegetables.svelte";

  let vegetablesList = [
    {
      name: "Radish",
      season: "Summer",
    },
    {
      name: "Onion",
      season: "Spring",
    },
    {
      name: "Carrot",
      season: "Summer",
    },
    {
      name: "Brussel sprouts",
      season: "Winter",
    },
    {
      name: "Cauliflower",
      season: "Winter",
    },
    {
      name: "Rocket",
      season: "Autumn",
    },
    {
      name: "Broccoli",
      season: "Summer",
    },
    {
      name: "Asparagus",
      season: "Spring",
    },
    {
      name: "Tomatoes",
      season: "Autumn",
    },
    {
      name: "Pumpkin",
      season: "Autumn",
    },
  ];
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main
    class="container flex justify-between mx-auto m-8 border-2 border-dashed rounded p-8"
  >
    <!-- CONTENU ICI -->
    <button
      class="px-3 py-2 bg-amber-600 rounded text-white "
      on:click={handleClick}
    >
      Show de list of the Vegetables 🥕<button />
    </button>
    <button
      class="px-10 py-2 bg-green-600 rounded text-white "
      on:click={handleClick}
    >
      Show me one Vegetable 🥕<button />
    </button>
  </main>
</div>

<style>
  .animation-image {
    @apply cursor-pointer duration-200;
  }

  .animation-image:hover {
    @apply scale-75;
  }
</style>
