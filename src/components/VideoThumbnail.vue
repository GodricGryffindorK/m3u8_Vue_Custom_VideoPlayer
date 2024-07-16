<template>
  <div class="video-thumbnail" :style="{ width: thumbWidth }">
    <v-img :src="imageUrl" :aspect-ratio="2" cover>
      <v-btn width="30" height="30" class="center-btn play-button" icon
        ><v-icon color="white" size="26">mdi-play</v-icon></v-btn
      >
    </v-img>
    <div class="caption">
      {{ caption }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    thumbWidth: {
      type: String,
      required: true,
      default: "262px",
    },
    imageUrl: {
      type: String,
      required: true,
    },
    caption: {
      type: String,
      default: "Watch the video",
    },
  },
};
</script>

<style>
.video-thumbnail {
  position: relative;
  display: inline-block;
  left: 50%;
  transform: translate(-50%, 0);
  border-radius: 5px;
  overflow: hidden;
}

.thumbnail-image {
  width: 100%;
  object-fit: cover;
  float: left;
  display: inline-block;
}

.play-button {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 50%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.play-button svg {
  fill: white;
}

.caption {
  position: relative;
  letter-spacing: 2px;
  line-height: 27px;
  float: left;
  display: inline-block;
  bottom: 0px;
  width: 100%;
  background-color: #262626;
  color: white;
  padding: 3px 10px;
  font-size: 11px;
  font-family: "PingFang SC";
  font-weight: 30;
}
</style>
