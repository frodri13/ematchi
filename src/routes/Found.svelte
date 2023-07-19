<script lang="ts">
    export let found: string[];
</script>

<div class="text-5xl flex items-center justify-center p-3">
    {#each found as emoji (emoji)}
        <span>{emoji}</span>
    {/each}
</div>