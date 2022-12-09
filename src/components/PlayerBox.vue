<template>
  <div class="playerBox">
    <div class="playPause">
      <button v-on:click="playPause" class="playPauseButton" :disabled=loading v-bind:class="(playing)?'playing':''">{{
          buttonLabel
      }}</button>
    </div>
  </div>
</template>
<script lang="ts">
import IcecastMetadataPlayer from "icecast-metadata-player"

export default {
  name: 'player-box',
  data: function () {
    return {
      buttonLabel: "Play",
      playing: false,
      loading: false,
      player: new IcecastMetadataPlayer(
        "https://radioadmin.lostcausegang.org/listen/lost_cause_radio/radio.mp3",
        {
          onStreamStart: () => {
            this.buttonLabel = "Pause" as any
            this.loading = false as any
          },
        },
      ),
    }
  },
  methods: {
    playPause() {
      if (this.playing == false) {
        this.loading = true
        this.buttonLabel = "Loading..."
        this.player.play()
        this.playing = true
      } else {
        this.player.stop()
        this.buttonLabel = "Play"
        this.playing = false
      }
    }
  }
}
</script>
<style>
.playerBox {
  display: inline-block;
  margin-left: 1em;
}

.playPauseButton {
  padding: 1em 3.5em;
  cursor: pointer;
  user-select: none;
  text-align: center;
  white-space: nowrap;
  text-decoration: none !important;
  text-transform: none;
  text-transform: capitalize;

  color: var(--color-snow);
  background-color: black;
  border: 0 none;
  font-size: 13px;
  font-weight: 500;
  line-height: 1.3;

  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;

  justify-content: center;
  align-items: center;
  flex: 0 0 160px;
}

.playing,
.playPauseButton:disabled {
  background-color: var(--color-dark);
}

.playPauseButton:hover {
  transition: all 150ms linear;
  opacity: .85;
}

.playPauseButton:active {
  transition: all 150ms linear;
  opacity: .75;
}

.playPauseButton:focus {
  outline: 1px dotted #959595;
  outline-offset: -4px;
}

@media only screen and (max-width: 375px) {
  .playerBox {
    margin: auto auto auto 2em;
  }
}
</style>
