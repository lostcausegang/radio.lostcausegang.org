<template>
    <div class="current-playlist">
        <marquee-text :key="currentSongTitle" :repeat=10>{{ currentPlaylistTitle }}<span
                class="separator">|</span></marquee-text>
    </div>
    <div class="playing-box">
        <div class="now-playing">
            <h1>Now playing</h1>
            <p>{{ currentSongTitle }}</p>
        </div>
        <div class="next-playing">
            <h1>Up next</h1>
            <p>{{ nextSongTitle }}</p>
        </div>
    </div>
</template>
<script lang="ts">
import NchanSubscriber from 'nchan'
import MarqueeText from 'vue-marquee-text-component'
export default {
    name: 'now-playing',
    components: {
        MarqueeText
    },
    data: function () {
        return {
            sub: new NchanSubscriber("https://radioadmin.lostcausegang.org/api/live/nowplaying/lost_cause_radio"),
            currentSongTitle: "LOADING...",
            currentPlaylistTitle: "LOADING...",
            nextSongTitle: "LOADING...",
        }
    },
    created() {
        let nowPlaying: any
        this.sub.on("message", (message: string) => {
            nowPlaying = JSON.parse(message)
            this.currentSongTitle = nowPlaying.now_playing.song.text
            this.currentPlaylistTitle = nowPlaying.now_playing.playlist
            this.nextSongTitle = nowPlaying.playing_next.song.text
        })
        this.sub.start()
    },
}
</script>
<style>
.current-playlist {
    color: black;
    font-size: 1.5em;
    border-bottom: 1px solid black;
    width: 100%;
}

.playing-box {
    padding: 3em 0 0 5em;
}

.now-playing p {
    color: black;
    font-family: Arial;
    font-size: 5em;
    width: 50%;
    line-height: 1em;
    text-transform: capitalize;
}

.now-playing h1 {
    color: black;
    font-family: 'Arial Black';
    margin-bottom: 0.5em;
    font-size: 10em;
    width: 50%;
    line-height: 0.7em;
}

.next-playing p {
    color: black;
    font-family: Arial;
    width: 35%;
    font-size: 2em;
    text-transform: capitalize;
}

.next-playing h1 {
    color: black;
    font-family: 'Arial Black';
    font-size: 4em;
    margin-top: 0.1em;
}

.separator {
    padding-left: 0.5em;
    padding-right: 0.5em;
}

@media only screen and (max-width: 810px) {

    .playing-box {
        padding: 2em;
        width: 100%;
    }

    .now-playing p,
    .next-playing p {
        width: 90%;
    }
}

@media only screen and (max-width: 670px) {
    .now-playing h1 {
        font-size: 6em;
    }

    .next-playing h1 {
        font-size: 3em;
    }
}

@media only screen and (max-width: 412px) {
    .now-playing h1 {
        font-size: 4.5em;
    }

    .now-playing p {
        font-size: 3em;
    }

    .next-playing h1 {
        font-size: 2em;
    }
}
</style>
