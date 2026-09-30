<script lang="ts">
    let { children, target, url }: { children: any; target: string; url: URL } = $props();

    const normalize = (path: string) => path.replace(/\/+$/, "") || "/";
    const active = $derived(normalize(url.pathname) === normalize(target));
</script>

<a href={target} class="text-xl">
    {@render children()}
    {#if active}
        <div
            class="relative h-0.5 w-full rounded-4xl bg-white/30"
            style="view-transition-name: nav-underline"
        ></div>
    {/if}
</a>
