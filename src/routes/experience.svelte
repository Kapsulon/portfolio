<script lang="ts">
    import { onMount } from "svelte";
    import "../style/index.scss";
    import Navbar from "$lib/navbar.svelte";
    import {createCard} from "$lib/languagecard.svelte";

    let cards:HTMLUListElement;
    let languages = [
        {
            name: "French",
            desc: "French is my main language.",
            level: "Native",
            icon: ""
        },
        {
            name: "English",
            desc: "English is my second language. I started learning English when I was 7 years old on my own and haven't stopped since.",
            level: "Fluent (920/990 TOEIC)",
            icon: ""
        },
        {
            name: "Korean",
            desc: "I just started learning Korean recently. I'm learning it on my own and I'm very excited to learn more languages.",
            level: "Beginner",
            icon: ""
        }
    ];
    onMount(() => {
        languages.forEach(language => {
            let card = createCard(language.name, language.desc, language.icon, language.level);
            cards.appendChild(card);
        });
    });
</script>

<head>
    <title>Kapsulon - Experience</title>
</head>

<Navbar />

<ul bind:this={cards}>

</ul>
