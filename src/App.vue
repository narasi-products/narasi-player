<template>
  <div id="app">
    <NarasiPlayer :options="videoOptions" @ready="player"/>
  </div>
</template>

<script>

import NarasiPlayer from './components/Player.vue'

export default {
  name: 'App',
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
  mounted() {
    
  }
}
</script>
