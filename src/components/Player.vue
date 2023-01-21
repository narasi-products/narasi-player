<template>
  <div>
    <video ref="videoPlayer" class="video-js"></video>
  </div>
</template>

<script>

import videojs from 'video.js';
import 'videojs-contrib-quality-levels';
import 'videojs-hls-quality-selector';
import 'videojs-mobile-ui';
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
    this.player = videojs(this.$refs.videoPlayer, this.options, () => {
      
      this.player.hlsQualitySelector({
          displayCurrentQuality: true,
      });

      this.player.mobileUi();
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