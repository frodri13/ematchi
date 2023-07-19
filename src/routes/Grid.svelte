<script lang="ts">
  import Square from "./Square.svelte";

  export let grid: string[];

  let a = -1;
  let b = -1;
  let reset_timeout: ReturnType<typeof setTimeout>;
</script>
<div class="grid grid-cols-4 grid-rows-4 h-full gap-[0.5em]">
    {#each grid as emoji, i}
        <Square 
          {emoji}
          selected={a === i || b === i} 

          on:click={() => {
            clearTimeout(reset_timeout)
              if(a === -1 && b === -1){
                 a = i;
              } else if (b === -1) {
                 b = i;

                if (grid[a] === grid[b]) {
                  // correct
                } else {
                  // incorrect
                  reset_timeout = setTimeout(() => {
                    a = b = -1;
                  }, 1000);
                }
              } else {
                b = -1;
                a = i;
              }
            }
          }/>
    {/each}

</div>