<script lang="ts">
    import { onMount } from "svelte";
    import "../style/index.scss";
    import "../style/languagecards.scss";
    import Navbar from "$lib/navbar.svelte";
    import {createCard} from "$lib/languagecard.svelte";

    let languagecards:HTMLUListElement;
    let languages = [
        {
            name: "French",
            desc: "French is my main language.",
            level: "Native",
            icon: "fr_flag.png"
        },
        {
            name: "English",
            desc: "English is my second language. I started learning English when I was 7 years old on my own and haven't stopped since.",
            level: "Fluent (920/990 TOEIC)",
            icon: "en_flag.png"
        },
        {
            name: "Korean",
            desc: "I started learning Korean recently. I'm learning it on my own and I'm very excited to learn more languages.",
            level: "Beginner",
            icon: "kr_flag.png"
        }
    ];
    onMount(() => {
        languages.forEach(language => {
            let card = createCard(language.name, language.desc, language.icon, language.level);
            languagecards.appendChild(card);
        });
    });
</script>

<head>
    <title>Kapsulon - Experience</title>
</head>

<Navbar />

<ul class="languages page" bind:this={languagecards}></ul>
