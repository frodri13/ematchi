<script lang="ts">
  import Square from "./Square.svelte";

  export let grid: string[];

</script>
<div class="grid grid-cols-4 grid-rows-4 h-full gap-[0.5em]">
    {#each grid as emoji}
        <Square {emoji} />
    {/each}

</div>