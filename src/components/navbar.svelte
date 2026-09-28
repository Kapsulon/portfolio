<script lang="ts">
    import { onMount } from "svelte";
    import { ArrowRight } from "@lucide/svelte";
    import { slide } from "svelte/transition";
    import NavbarLink from "./navbar-link.svelte";

    let { url }: { url: URL } = $props();

    const NAV_HEIGHT = 64;
    let theme = $state<"light" | "dark">("light");

    onMount(() => {
        const sections = Array.from(document.querySelectorAll<HTMLElement>("[data-nav-theme]"));
        if (sections.length === 0) return;

        let ticking = false;
        const updateTheme = () => {
            for (const section of sections) {
                const rect = section.getBoundingClientRect();
                if (rect.top <= NAV_HEIGHT && rect.bottom > NAV_HEIGHT) {
                    theme = section.dataset.navTheme === "dark" ? "dark" : "light";
                    break;
                }
            }
            ticking = false;
        };

        const onScroll = () => {
            if (!ticking) {
                ticking = true;
                requestAnimationFrame(updateTheme);
            }
        };

        updateTheme();
        window.addEventListener("scroll", onScroll, { passive: true });
        window.addEventListener("resize", onScroll);

        return () => {
            window.removeEventListener("scroll", onScroll);
            window.removeEventListener("resize", onScroll);
        };
    });
</script>

<nav
    class="fixed top-0 flex h-16 w-full flex-row items-center justify-between px-8 transition-colors duration-300 {theme ===
    'dark'
        ? 'text-black'
        : 'text-white'}"
>
    <div
        class="pointer-events-none absolute inset-x-0 top-0 z-0
           h-full
           mask-[linear-gradient(to_bottom,black_0%,transparent_100%)] backdrop-blur-xl"
    ></div>
    <a href="/" class="z-1 text-xl">Kapsulon</a>
    <div class="z-1 flex flex-row space-x-12">
        <NavbarLink target="/work" {url}>Work</NavbarLink>
        <NavbarLink target="/services" {url}>Services</NavbarLink>
        <NavbarLink target="/about" {url}>About</NavbarLink>
    </div>
    <a href="/contact" class="z-1 flex flex-row items-center justify-center space-x-1 text-xl">
        <span>Contact</span>
        <ArrowRight />
    </a>
</nav>
