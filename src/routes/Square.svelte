<script lang="ts">
  import { get_twemoji_url } from "./utils";

    export let emoji: string;
    export let selected: boolean;
    export let found: boolean;
</script>
<div class="bg-gray-200 text-7xl flex justify-center items-center" class:flipped={selected}>
    <button on:click class="absolute w-full h-full"/>
    {#if !found}
        <img class="pointer-events-none w-10 h-10" alt={emoji} src={get_twemoji_url(emoji)}/>
    {/if}
</div>  

<style>
    .flipped button {
        background: red;
    }
</style>