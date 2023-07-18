<script>
  import Square from "./Square.svelte";

</script>
<div class="grid grid-cols-4 grid-rows-4 h-full gap-[0.5em]">
    {#each Array(16) as _}
        <Square />
    {/each}

</div>