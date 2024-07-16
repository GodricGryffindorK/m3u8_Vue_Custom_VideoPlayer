<template>
  <v-container class="video-player-section">
    <div class="video-container">
      <video
        @pause="handlePause"
        @ended="handlePause"
        @keyup="changeSpeed"
        ref="video"
        :poster="preview"
        :controls="!isPaused"
        :title="title"
        @click="togglePlay"
        class="video-element"
      >
        <source :src="videoSource" type="application/x-mpegURL" />
      </video>
      <button v-if="isPaused" class="custom-play-button" @click="play">
        &#9658;
      </button>
    </div>
    <div class="video-caption">{{ caption }}</div>
    <v-btn size="small" rounded="xl" @click="jumpToTime(10)" class="seek-btn"
      >00:10</v-btn
    >
    <v-btn size="small" rounded="xl" @click="jumpToTime(20)" class="seek-btn"
      >00:20</v-btn
    >
    <v-btn size="small" rounded="xl" @click="jumpToTime(50)" class="seek-btn"
      >00:50</v-btn
    >
    <v-btn size="small" rounded="xl" @click="jumpToTime(70)" class="seek-btn"
      >01:10</v-btn
    >
  </v-container>
</template>

<script>
import { defineComponent, ref, onMounted, watch } from "vue";
import Hls from "hls.js";

export default defineComponent({
  props: {
    videoUrl: {
      type: String,
      required: true,
    },
    caption: {
      type: String,
      required: true,
    },
    preview: {
      type: String,
      required: true,
    },
  },
  setup(props) {
    const isPaused = ref(true);
    const video = ref(null);
    const previewImageLink = ref(props.preview);
    const videoSource = ref(props.videoUrl);
    const title = ref("");

    const handlePause = () => {
      const currentTime = video.value ? video.value.currentTime : 0;
      isPaused.value = true;
      console.log("Paused at:", currentTime);
    };

    const play = () => {
      if (video.value) {
        video.value.play();
        isPaused.value = false;
      }
    };

    const togglePlay = () => {
      if (video.value.paused) {
        play();
      } else {
        video.value.pause();
      }
    };

    const changeSpeed = (e) => {
      if (e.key === "w" && video.value) {
        video.value.playbackRate += 0.25;
      } else if (e.key === "s" && video.value) {
        video.value.playbackRate -= 0.25;
      }
    };

    const jumpToTime = (time) => {
      if (video.value) {
        video.value.currentTime = time;
      }
    };

    // Initialize video player with HLS.js
    const initializeVideoPlayer = () => {
      if (Hls.isSupported()) {
        const hls = new Hls();
        hls.loadSource(videoSource.value);
        hls.attachMedia(video.value);
        video.value.muted = false;
        video.value.currentTime = 0; // Set initial playback position
        video.value.addEventListener("canplay", () => {
          // Video can play, start playing if autoPlay is true
          if (!isPaused.value) {
            video.value.play();
          }
        });
      } else if (video.value.canPlayType("application/vnd.apple.mpegurl")) {
        video.value.src = videoSource.value;
        video.value.addEventListener("loadedmetadata", () => {
          video.value.currentTime = 0;
          if (!isPaused.value) {
            video.value.play();
          }
        });
      }
    };

    // Watch for changes in video source
    watch(
      () => props.videoUrl,
      () => {
        videoSource.value = props.videoUrl;
        initializeVideoPlayer();
      }
    );

    onMounted(() => {
      initializeVideoPlayer();
    });

    return {
      isPaused,
      video,
      previewImageLink,
      videoSource,
      title,
      handlePause,
      play,
      togglePlay,
      changeSpeed,
      jumpToTime,
    };
  },
});
</script>

<style>
/* Add your custom styles if needed */
.video-player-section {
  padding: 0 16px;
}
.video-container {
  position: relative;
  width: 100%;
  border-radius: 12px;
  overflow: hidden;
}

.video-element {
  width: 100%;
  height: auto;
  border-radius: 10px;
}

.custom-play-button {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: rgba(0, 0, 0, 0.5);
  padding-left: 3px;
  color: white;
  border: none;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  font-size: 30px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}

.custom-play-button:hover {
  background: rgba(0, 0, 0, 0.7);
}

.video-caption {
  padding: 3px 0 10px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  font-size: 13px;
  color: white;
}

.seek-btn {
  margin: 10px 5px 20px 0;
  background: #01d6be;
}
</style>
