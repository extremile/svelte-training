<script>
  import { onMount } from "svelte";
  import BlaguesAPI from "blagues-api";

  import "./assets/css/style.css";

  const apiKey =
    "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiOTIwOTc2ODE2NzQxNzA3Nzg3IiwibGltaXQiOjEwMCwia2V5IjoibHh1cGVEalN4djFjSmlGTkNuQkphbUVCNnhDQ2s5ejdSRFdVbloyQjlRNFB0eEJDZXkiLCJjcmVhdGVkX2F0IjoiMjAyMi0wNi0wOFQxMjowMDoyNCswMDowMCIsImlhdCI6MTY1NDY4OTYyNH0.zka3DecZ6dv5Gg3yax259fDWOU1bG3u_v7s6AR_6GDE";
  let joke;
  let answer;

  onMount(() => {
    setTimeout(async () => {
      const res = await fetch("https://www.blagues-api.fr/api/random", {
        headers: { Authorization: `Bearer ${apiKey}` },
      });
      let response = await res.json();
      answer = response.answer;
      joke = response.joke;
      let id = response.id;
      console.log(response);
      console.log(joke, answer, id);
    }, 500);
  });

  const refreshJoke = () => {
    joke = "";
    setTimeout(async () => {
      const res = await fetch("https://www.blagues-api.fr/api/random", {
        headers: { Authorization: `Bearer ${apiKey}` },
      });
      joke = (await res.json()).joke;
    }, 500);
  };
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/svelte-logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <!-- CONTENU ICI -->
    {#if joke}
      <p class="my-4 ml-2 italic font-bold">"{joke}"</p>
      <p class="py-1 text-center text-xl bg-black hover:bg-transparent">
        "{answer}"
      </p>
      <button
        class="px-4 py-2 mt-2 text-sm font-bold text-white bg-orange-600 duration-200 rounded-lg hover:bg-orange-400"
        on:click={refreshJoke}>One more...</button
      >
    {:else}
      <p class="text-4xl">Loading</p>
    {/if}
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
