Narasi Player for Streaming VOD & Live base on [Video.js](https://videojs.com).
## Setup
```sh
yarn add narasi-player
# Using npm
npm install narasi-player
```

## Usage
```html
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
        // adTagUrl: "https://pubads.g.doubleclick.net/gampad/ads?iu=/21775744923/external/single_ad_samples&sz=640x480&cust_params=sample_ct%3Dlinear&ciu_szs=300x250%2C728x90&gdfp_req=1&output=vast&unviewed_position_start=1&env=vp&impl=s&correlator=",
        textTrackSettings: true,
        autoplay: false,
        controls: true,
        muted: true,
        poster: 'https://example.com/poster.png',
        sources: [
          {
            src: 'https://example.com/manifest.m3u8',
            type: 'application/x-mpegURL'
          }
        ], 
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
```

## Referency API
See [Configuration Reference](https://docs.videojs.com/).
See [IMA SDK for Ads](https://github.com/googleads/videojs-ima/).
