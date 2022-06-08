<script>
  import "./assets/css/style.css";
  import { fly, fade } from "svelte/transition";

  let name = "";
  $: disabled = name.length > 3 ? false : true;

  let deathList = [];
  const killEvent = () => {
    deathList = [...deathList, name];
    name = "";
  };
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >
    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <!-- CONTENU ICI -->
    <h1 class="title primary">death note</h1>
    <form class="my-4 shadow-sm p-8" on:submit|preventDefault={killEvent}>
      <div class="form-control input">
        <label for="name"> Ajouter le nom de qulequ'un</label>
        <input type="text" id="name" bind:value={name} />
      </div>
      <button type="submit" {disabled} class="btn primary mt-4">Ajouter</button>
    </form>
    <div class="bg-black text-white shadow-md rounded-md p-8">
      {#each deathList as death}
        <p
          class="mt-2 text-xl text-center"
          in:fly={{ y: -200, duration: 1000, delay: 100 }}
          out:fade
        >
          {death}
        </p>
      {:else}
        <p class="text-3xl text-center">No One To Kill</p>
      {/each}
      {#if deathList.length}
        <button
          class="btn cancel mt-8 mx-auto block"
          on:click={() => (deathList = [])}>Save Their Live</button
        >
      {/if}
    </div>
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
