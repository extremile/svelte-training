<script>
  import "./assets/css/style.css";

  let name = "Bernard";
  let src = "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTAqam9v2iw9sA8r1lfKQmKA86guUY0MHaCsw&usqp=CAU";
  let classe = `${name === "Bernard" ? 'w-64' : 'w-4'}`;
</script>

<div class="bg-slate-50 flex flex-col min-h-screen">
  <header
    class="mt-6 mx-8 shadow-md rounded-md flex justify-center bg-white overflow-hidden"
  >

    <img src="/logo.png" alt="logo" class="w-16 animation-image" />
  </header>
  <main class="container mx-auto m-8 border-2 border-dashed rounded p-8">
    <!-- CONTENU ICI -->
    
    Hello {name + ' loempia'} !
    <img src={src} class={classe} alt="Bernard sans dent">
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
