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
        // adTagUrl: "https://pubads.g.doubleclick.net/gampad/ads?iu=/21775744923/external/single_ad_samples&sz=640x480&cust_params=sample_ct%3Dlinear&ciu_szs=300x250%2C728x90&gdfp_req=1&output=vast&unviewed_position_start=1&env=vp&impl=s&correlator=",
        textTrackSettings: true,
        autoplay: false,
        controls: true,
        muted: true,
        poster: 'https://storage.googleapis.com/narasi-production.appspot.com/files/2023/01/19/video/eka-kurniawan-trending-karena-ada-yang-salah-paham-kutipan-novelnya---narasi-newsroom-1674128618/poster.png',
        sources: [
          {
            src: 'https://storage.googleapis.com/narasi-production.appspot.com/files/2023/01/19/video/eka-kurniawan-trending-karena-ada-yang-salah-paham-kutipan-novelnya---narasi-newsroom-1674128618/manifest.m3u8'
          }
        ],
        
      }
    }
  },
  methods: {
    player(e) {
      console.log(e);
    }
  },
  mounted() {
    
  }
}
</script>

<style lang="css">
.video-js {
  width: 100%;
}
</style>
