<script lang="ts">
    export let emoji: string;
    export let selected: boolean;
    export let found: boolean;
</script>
<div class="bg-yellow-200 text-7xl flex justify-center items-center" class:flipped={selected}>
    <button on:click class="absolute w-full h-full"/>
    {#if !found}
        <span class="pointer-events-none">{emoji}</span>
    {/if}
</div>  

<style>
    .flipped button {
        background: red;
    }
</style>