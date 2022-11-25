<template>
    <div class="now-playing-container">
        <div class="now-playing">
            <marquee-text :key="currentSongTitle"
:duration=currentSongTitle.length>
                {{ currentSongTitle }} <span class="songDivider">>></span>
            </marquee-text>
        </div>
        <div class="playlist">Live: {{ currentPlaylistTitle }}</div>
        <div class="queueTitle">Up Next</div>
        <div class="metadataQueue">
            {{ nextSongTitle }}
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
.now-playing-container {
    width: 100%;
}

.now-playing {
    text-align: center;
    font-family: alarmClock, 'Courier New', Courier, monospace;
    font-size: 3em;
    margin: 1em auto 0 auto;
    background-color: #000;
    height: 2em;
    line-height: 2em;
    color: #77b791;
    text-shadow: 5px 3px 7px rgba(119, 183, 145, 0.80);
    box-shadow: 1px 1px 9px black;
    width: 50%;
    border-radius: 10px;
}

.playlist {
    text-align: center;
    font-family: Helvetica, Arial, sans-serif;
    font-weight: bold;
    margin-top: 2em;
    color: #fff8e4;
    text-shadow: 1px 1px 4px rgba(79, 71, 50, 0.75);
}

.queueTitle {
    font-size: 1.7em;
    font-family: Helvetica;
    margin: 2em auto 1em auto;
    font-weight: bold;
    text-align: center;
    color: #fff8e4;
    text-shadow: 1px 1px 4px rgba(79, 71, 50, 0.75);
}

.metadataQueue {
    text-align: center;
    font-size: 1.25em;
    margin-bottom: 2em;
    font-weight: 600;
    font-family: 'Courier New', Courier, monospace;
    color: #fff8e4;
    text-shadow: 1px 1px 4px rgba(79, 71, 50, 0.75);
}

.songDivider {
    padding-left: 0.5em;
    padding-right: 0.5em;
}

/* Move it (define the animation) */
@-moz-keyframes horizontally {
    0% {
        -moz-transform: translateX(50%);
    }

    100% {
        -moz-transform: translateX(-50%);
    }
}

@-webkit-keyframes horizontally {
    0% {
        -webkit-transform: translateX(50%);
    }

    100% {
        -webkit-transform: translateX(-50%);
    }
}

@keyframes horizontally {
    0% {
        -moz-transform: translateX(50%);
        /* Browser bug fix */
        -webkit-transform: translateX(50%);
        /* Browser bug fix */
        transform: translateX(50%);
    }

    100% {
        -moz-transform: translateX(-50%);
        /* Browser bug fix */
        -webkit-transform: translateX(-50%);
        /* Browser bug fix */
        transform: translateX(-50%);
    }
}
</style>