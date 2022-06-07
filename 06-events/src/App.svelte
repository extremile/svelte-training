<script>
  import "./assets/css/style.css";
  import ImageDetail from "./ImageDetail.svelte";

  let scale = 1;

  const handleWheel = (e) => {
    if (e.deltaY < 0) {
      scale += 0.1;
    } else {
      scale -= 0.1;
    }
  };

  let imageDetails = [
    {
      id: 1,
      src: "https://picsum.photos/200/300",
      name: "LittleBig.png",
      size: "3.8MB",
    },
    {
      id: 2,
      src: "https://picsum.photos/201/300",
      name: "DestinyChild.png",
      size: "1.0MB",
    },
    {
      id: 3,
      src: "https://picsum.photos/202/300",
      name: "bigDuck.heic",
      size: "302KB",
    },
    {
      id: 4,
      src: "https://picsum.photos/203/300",
      name: "interstellar-385421555.png",
      size: "1.2GB",
    },
  ];

  const handleDelete = (e) => {
    console.log(e);
    console.log(e.detail); //on recoit les parametres du dispatch deqns le détail
    imageDetails = imageDetails.filter((img) => img.id != e.detail);
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
    <p
      on:wheel={(e) => (e.deltaY < 0 ? (scale += 0.1) : (scale -= 0.1))}
      class="text-center"
      style="transform: scale({scale})"
    >
      Ceci es le painde goulagwe
    </p>
    <button
      class="m-8 p-2 bg-red-600 text-white"
      on:click|once={() => alert("Au gogole")}
    >
      Alerte au gogole
    </button>

    <ul class="grid grid-cols-2 gap-x-4 gap-y-8 mt-8 lg:grid-cols-4">
      {#each imageDetails as detail}
        <!-- <ImageDetail name={ImageDetail.name} src={ImageDetail.src} size={ImageDetail.size}/> -->
        <ImageDetail {...detail} on:deleteImg={handleDelete} />
      {/each}
    </ul>
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
