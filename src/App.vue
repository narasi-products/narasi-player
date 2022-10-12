<template>
  <div id="app">
    <NarasiPlayer :options="videoOptions"/>
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
        poster: 'https://statik.tempo.co/data/2019/10/31/id_885345/885345_720.jpg',
        sources: [
          {
            src: 'https://d322b885qvsbxg.cloudfront.net/GTV2021.m3u8', type: 'application/x-mpegURL'
          }
        ],
        html5: {
          nativeAudioTracks: true,
          nativeVideoTracks: true,
          nativeTextTracks: true
        },
        
      }
    }
  }
}
</script>
