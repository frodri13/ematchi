<script lang="ts">
  import { get_twemoji_url } from "./utils";

    export let emoji: string;
    export let selected: boolean;
    export let found: boolean;
</script>
<div id="square" class="bg-gray-200 text-7xl flex justify-center items-center" class:flipped={selected || found}>
    <button on:click class="absolute w-full h-full bg-[#eee] border-spacing-0 border-r-2"/>

    <div class="bg-white border-spacing-1 border-solid border-[#eee] absolute w-full h-full" id="bg"/>
    {#if !found}
        <img class="pointer-events-none w-10 h-10" alt={emoji} src={get_twemoji_url(emoji)}/>
    {/if}
</div>  

<style>
    #square {
        transition: transform 0.4s;
        transform-style: preserve-3d;
    }
    .flipped {
        transform: rotateY(180deg);
    }

    img,   #bg  {
        transform: rotateY(180deg);
        backface-visibility: hidden;
    }
    button {
        backface-visibility: hidden;
        font-size: inherit;
    }
</style>