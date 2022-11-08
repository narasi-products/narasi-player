<template>
<div>
    <narasi-player :options="videoOptions" @ready="player"/>
</div>
</template>

<script>

import 'narasi-player/dist/narasi-player.css'
import NarasiPlayer from "narasi-player";

export default {
  components: {
    NarasiPlayer
  },
  data() {
    return {
      videoOptions: {
        autoplay: false,
        controls: true,
        preload: "auto",
        width: '873px',
        height: '491px',
        poster: 'https://storage.googleapis.com/narasi-non-production.appspot.com/vod/adbf9393bb09fe1b1ed54d252075509936578a00/poster.jpeg',
        sources: [
          {
            src: 'https://storage.googleapis.com/narasi-non-production.appspot.com/vod/adbf9393bb09fe1b1ed54d252075509936578a00/playlist.m3u8', type: 'application/x-mpegURL'
          }
        ],
        html5: {
          nativeAudioTracks: true,
          nativeVideoTracks: true,
          nativeTextTracks: true
        },
        
      }
    }
  },
  methods: {
    player(player) {
      player.on('play', (e) => {
        console.log(e);
      })
    }
  },
}
</script>
