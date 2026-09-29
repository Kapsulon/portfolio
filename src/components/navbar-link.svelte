<script lang="ts">
    let { children, target, url }: { children: any; target: string; url: URL } = $props();
</script>

<a href={target} class="text-xl">
    {@render children()}
    {#if url.pathname.endsWith(target)}
        <div
            class="relative h-0.5 w-full rounded-4xl bg-white/30"
            style="view-transition-name: nav-underline"
        ></div>
    {/if}
</a>
