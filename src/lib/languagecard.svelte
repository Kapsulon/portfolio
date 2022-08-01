<script lang="ts" context="module">
    export function createCard(name:string, description:string, logo:string, duration:any):HTMLElement {
        let card:HTMLElement = document.createElement("li")
        card.innerHTML = `
            ${name}
        `
        return card
    }
</script>
