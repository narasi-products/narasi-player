<template>
  <div>
    <video
      preload="auto" 
      webkit-playsinline
      ref="videoPlayer"
      controls="false"
      class="video-js"
    ></video>
  </div>
</template>

<script>
import videojs from "video.js";
import "videojs-contrib-quality-levels";
import "videojs-hls-quality-selector";
import "/public/theme/narasi/video-js.css";
import "/public/theme/narasi/narasi.css";
import "videojs-mobile-ui";
import "videojs-mobile-ui/dist/videojs-mobile-ui.css";
import 'videojs-contrib-ads';
import 'videojs-ima';

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
  methods: {},
  mounted() {
    const container = this.$refs.videoPlayer;
    this.player = videojs(container, this.options, () => {
      container.playsinline = "playsinline";
      this.player.hlsQualitySelector({
        displayCurrentQuality: true,
      });

      this.player.playsinline(true);
      
      this.player.mobileUi();
      
      if (this.options.adTagUrl !== undefined) {
        this.player.ima({
          adTagUrl: this.options.adTagUrl,
        })
      }

    });

    this.player.on("touchstart", (e) => {
      if (e.target.classList[0].includes("vjs-touch-overlay")) {       
        if (this.player.paused()) {
          this.player.play();
        } else {
          this.player.pause();
        } 
      }
    });

    this.player.on("ready", () => {
      this.$emit("ready", this.player);
    });

  },
  beforeDestroy() {
    if (this.player) {
      this.player.dispose();
    }
  },
};
</script>