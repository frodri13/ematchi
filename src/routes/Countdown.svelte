<script lang="ts">
    export let remaining: number;
    export let duration: number;
</script>

<div class="flex items-center gap-[1em]" id="countdown">
    <button class="text-[8em] w-[1em] h-[1em] bg-transparent border-none">
        <svg class="absolute w-full h-full left-0 top-0" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><title>pause</title><path d="M14,19H18V5H14M6,19H10V5H6V19Z" fill="#999" /></svg> 
    </button>

        
    <div class="flex-1 h-[1em] bg-[#ccc]" id="duration">
        <div class="absolute h-full bg-[#999]" id="remaining"
        style="--p: {remaining / duration}"/>
    </div>
</div>

<style>
    #remaining {
        width: calc(100% * var(--p));
    }
</style>