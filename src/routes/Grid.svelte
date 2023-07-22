<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import Square from "./Square.svelte";

  export let grid: string[];
  export let found: string[];

  let a = -1;
  let b = -1;

  const dispatch = createEventDispatcher();
  let reset_timeout: ReturnType<typeof setTimeout>;
</script>
<div id="grid" class="grid grid-cols-4 grid-rows-4 h-full gap-[0.5em]">
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
                  dispatch('found', {
                    emoji
                  })
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
          }
          found={found.includes(emoji)}
          />
    {/each}

</div>

<style>
  #grid {
    perspective: 100vw;
  }
</style>