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
        autoplay: false,
        controls: true,
        preload: "auto",
        width: '873px',
        height: '491px',
        poster: 'https://example.com/poster.jpeg',
        sources: [
          {
            src: 'https://example.com/playlist.m3u8', type: 'application/x-mpegURL'
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
```

## Referency API
See [Configuration Reference](https://docs.videojs.com/).
