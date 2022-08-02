<script lang="ts" context="module">
    import "../style/languagecards.scss";
    export function createCard(name:string, description:string, logo:string, duration:any):HTMLElement {
        let card:HTMLElement = document.createElement("li")
        if (typeof duration == "string") {
            card.innerHTML = `
                <div class="card">
                    <div class="card-header">
                        <h3>${name}</h3>
                    </div>
                    <div class="card-body">
                        <p>${description}</p>
                    </div>
                    <div class="card-footer">
                        <p>Level: ${duration}</p>
                    </div>
                </div>
            `
        }
        return card
    }
</script>
