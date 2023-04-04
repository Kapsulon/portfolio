<script lang="ts">
    import "../style/index.scss";
    import Navbar from "$lib/navbar.svelte";
    import Spotifyspy from "$lib/spotifyspy.svelte";
    import {getAge} from "$lib/autoage.svelte";

    let birthday:Date = new Date("2003-08-05");
    birthday.setHours(12, 10);

    let programmingSince:Date = new Date("2016-03-15");
</script>

<head>
    <title>Kapsulon - Home</title>
</head>

<Navbar />

<div class="textbox">
    <p class="name">
        Kapsulon
    </p>
    <p class="description">
        My name is <span class="highlight">Théo</span>, I am <span class="highlight">{getAge(birthday)}<span class="blinking-cursor">_</span> years old</span>, I have been programming for <span class="highlight">{getAge(programmingSince)}<span class="blinking-cursor">_</span> years</span>, both as a <span class="highlight">passion</span> and a <span class="highlight">student</span>. <br/>
        I am currently studying <span class="highlight">Computer Science</span> at <span class="highlight"><u>Epitech</u></span>.
    </p>
    <Spotifyspy />
</div>
