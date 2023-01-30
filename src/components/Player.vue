<template>
  <div>
    <video webkit-playsinline ref="videoPlayer" class="video-js"></video>
  </div>
</template>

<script>

import videojs from 'video.js';
import 'videojs-contrib-quality-levels';
import 'videojs-hls-quality-selector';
import '/public/theme/narasi/video-js.css';
import '/public/theme/narasi/narasi.css';

export default {
  name: "narasi-player",
  props: {
    options: {
      type: Object,
      default() {
        return {};
      },
      
    },
  },
  data() {
    return {
      player: null,
    };
  },
  mounted() {
    const container = this.$refs.videoPlayer;
    this.player = videojs(container, this.options, () => {
      
      container.playsinline = "playsinline";
      this.player.hlsQualitySelector({
          displayCurrentQuality: true,
      });

      this.player.playsinline(true);
    });
    
    this.player.on('ready', () => {
      this.$emit('ready', this.player);
    })

  },
  beforeDestroy() {
    if (this.player) {
      this.player.dispose();
    }
  },
};
</script>