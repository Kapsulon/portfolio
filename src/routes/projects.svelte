<script lang="ts">
    import "../style/index.scss";
    import Navbar from "$lib/navbar.svelte";
</script>

<head>
    <title>Kapsulon - Projects</title>
</head>

<Navbar />

<div class="projects page">
    <div class="project-card">
        <a href="https://kapsulon.itch.io/dualitys-descent" target="_blank">
            <span class="project-name">Duality's Descent</span>
            <br/>
            <span class="project-desc">A game I made with a friend for a 48H Game Jam</span>
    </div>
    <div class="project-card">
        <a href="https://github.com/Kapsulon/klc" target="_blank">
            <span class="project-name">Kapsulon's Logo Creator</span>
            <br/>
            <span class="project-desc">A project that I use to change the colors of my logo from time to time, compiled automatically via github actions.</span>
        </a>
    </div>
    <div class="project-card">
        <a href="https://github.com/Kapsulon" target="_blank">
            <span class="project-name">My Github</span>
            <br/>
            <span class="project-desc">My Github profile, where I host all my projects.</span>
        </a>
    </div>
</div>
