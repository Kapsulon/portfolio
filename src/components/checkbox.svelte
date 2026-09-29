<script lang="ts">
    import { IconCheck } from "@tabler/icons-svelte";

    let { id }: { id: string } = $props();
    let checked: boolean = $state(false);
    let focused: boolean = $state(false);
</script>

<div class="relative mr-1 h-4 w-4">
    <input type="checkbox" class="h-full w-full opacity-0" {id} bind:checked bind:focused />
    <span
        class="pointer-events-none absolute inset-0 flex h-full w-full items-center justify-center rounded-xs border
        {checked ? 'border-cyan-800' : 'border-neutral-500'}
        {checked ? 'bg-cyan-500' : 'bg-neutral-100'}
        transition-colors
        {focused ? 'outline outline-neutral-50' : ''}
        "
    >
        {#if checked}
            <IconCheck stroke="4" />
        {/if}
    </span>
</div>
