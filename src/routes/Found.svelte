<script lang="ts">
    import { get_twemoji_url } from "./utils";
    export let found: string[];
</script>

<div class="text-5xl flex items-center justify-center p-3">
    {#each found as emoji (emoji)}
        <img class="pointer-events-none w-10 h-10" alt={emoji} src={get_twemoji_url(emoji)}/>

    {/each}
</div>