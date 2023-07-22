<script lang="ts">
  import { onMount } from "svelte";
  import Countdown from "./Countdown.svelte";
import Found from "./Found.svelte";
  import Grid from "./Grid.svelte";
  import { levels, type Level } from "./levels";
  import { shuffle } from "./utils";
  
  let level = levels[0];

  let size: number = level.size
  let grid: string[] = create_grid(level);
  let found: string[] = [];
  let remaining: number = level.duration;
  let duration: number = level.duration;
  let playing: boolean = false;

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

    return shuffle(pairs);
  }

  function countdown() {
      const start = Date.now();
      let reamining_at_start = remaining;

      function loop(){
        if (playing) return;
        requestAnimationFrame(loop);

        remaining = reamining_at_start - (Date.now() - start);

        if(remaining <= 0) {
            playing = false;
        }
      }
      loop();
    }

    onMount(countdown);
</script>
<div class="flex flex-col items-center justify-center h-full text-dynamic">
   
    <div class="w-[80em] h-[10em">
        <Countdown {remaining} duration={level.duration} />
    </div>

    <div class="w-[80em] h-[80em]">
        <Grid {grid} on:found={(e) =>{
          found = [...found, e.detail.emoji]
        }}
        {found}
        />
    </div>

    <div class="w-[80em] h-[10em]">
        <Found {found}/>
    </div>
</div>

