<script lang="ts">
    import { page } from "$app/stores";
    import "../style/navbar.scss";

    let pages = [
        {
            name: "Home",
            url: "/",
            favicon: "fa-solid fa-house navbar-icon"
        },
        {
            name: "Languages",
            url: "/languages",
            favicon: "fa-solid fa-earth-europe navbar-icon"
        },
        {
            name: "Projects",
            url: "/projects",
            favicon: "fa-solid fa-code navbar-icon"
        },
        {
            name: "Contact",
            url: "/contact",
            favicon: "fa-solid fa-envelope navbar-icon"
        }
    ];
    let path:string = $page.url.pathname;
</script>

<ul class="navbar">
    {#each pages as page}
        {#if page.url == path}
            <li class="navbar">
                <b><a href={page.url} class="active"><i class={page.favicon}></i>{page.name}</a></b>
            </li>
        {:else}
            <li class="navbar">
                <a href={page.url}><i class={page.favicon}></i>{page.name}</a>
            </li>
        {/if}
    {/each}
</ul>
