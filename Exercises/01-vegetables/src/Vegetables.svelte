<script>
  export let vegetables;
</script>

{#each vegetables as { name, saison }, index}
  <p class="mt-1 ml-2">{index + 1}. {name} ({saison})</p>
{/each}
