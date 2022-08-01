<script lang="ts">
    interface SpotifyData {
        track: string;
        album: string;
        artist: string;
        image: string;
    }

    let spotifyData: SpotifyData = {
        track: "Concentrating...",
        album: "Currently not listening to Spotify",
        artist: "Currently not listening to Spotify",
        image: "",
    };

    async function Heartbeat() {
        try {
            let discord_id: string = "257607907338616843";
            const response = await fetch(
                "https://api.lanyard.rest/v1/users/" + discord_id
            );
            const data = await response.json();
            if (data.data.listening_to_spotify) {
                spotifyData.track = data.data.spotify.song;
                spotifyData.album = data.data.spotify.album;
                spotifyData.artist = data.data.spotify.artist;
                spotifyData.image = data.data.spotify.album_art_url;
                return true;
            } else {
                spotifyData.track = "Concentrating...";
                spotifyData.album = "Currently not listening to Spotify";
                spotifyData.artist = "Currently not listening to Spotify";
                spotifyData.image = "";
                return false;
            }
        } catch(error) {
            console.log(error);
            return false;
        }
    }
    Heartbeat();
    let hb: NodeJS.Timer = setInterval(Heartbeat, 1000);
</script>

<div class="spotifyspy">
    <div>
        {#if spotifyData.track != "Concentrating..."}
            <i class="fa-solid fa-volume-high"></i>
        {:else}
            <i class="fa-solid fa-volume-xmark"></i>
        {/if}
    </div>
    <div class="spotifyspytext">
        <p class="spotifyspytextdivider">{spotifyData.track}</p>
        <p class="spotifyspytextdivider album_title"><i class="fa-brands fa-spotify"></i> {spotifyData.artist}</p>
    </div>
</div>