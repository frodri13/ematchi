<script lang="ts">
  import Grid from "./Grid.svelte";
  import { levels, type Level } from "./levels";
  
  let level = levels[0];

  let size: number = level.size
  let grid: string[] = create_grid(level);
  let found: string[] = [];

  function create_grid(level: Level){
    const copy = level.emojis.slice();
    const pairs: string[] = [];

    for(let i = 0; i < level.size ** 2 / 2; i += 1){
        const index = Math.floor(Math.random() * copy.length);
        const emoji = copy[index];

        copy.splice(index, 1);
        pairs.push(emoji);
    }

    pairs.push(...pairs);

    return pairs;
  }


</script>
<div class="flex flex-col items-center justify-center h-full text-dynamic">
   
    <div class="w-[80em] h-[10em] bg-purple-600">

    </div>

    <div class="w-[80em] h-[80em] bg-teal-400">
        <Grid {grid}/>
    </div>

    <div class="w-[80em] h-[10em] bg-purple-600">

    </div>
</div>

