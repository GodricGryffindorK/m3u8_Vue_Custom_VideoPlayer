<template>
  <v-container>
    <!-- Header -->
    <div class="headline">精彩推荐</div>

    <!-- Grid Layout -->
    <v-row dense justify="center">
      <!-- First Column -->
      <v-col v-for="(video, index) in videos" :key="index" cols="6">
        <!-- Video Thumbnail Component -->
        <VideoThumbnail
          thumb-width="100%"
          :image-url="video.image"
          :caption="video.title"
          @click="() => onClick(video.video, video.title, video.image)"
        />
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import VideoThumbnail from "./VideoThumbnail.vue"; // Adjust path as per your project structure

export default defineComponent({
  components: {
    VideoThumbnail,
  },
  props: {
    onClick: {
      type: Function as PropType<
        (videoUrl: string, caption: string, image: string) => void
      >,
      required: true,
    },
  },
  data(): {
    columns: number;
    videos: { id: string; title: string; image: string; video: string }[];
  } {
    return {
      columns: 6,
      videos: [
        {
          id: "1",
          title: "标题1",
          image: "v-thumbnail.jpg",
          video:
            "https://m3u.haiwaikan.com/xm3u8/76762beb45c79951cf49d40b6bca77d6aaf720e46c1579ed4dffce395884fb289921f11e97d0da21.m3u8",
        },
        {
          id: "2",
          title: "标题2",
          image: "v-thumbnail.jpg",
          video:
            "https://m3u.haiwaikan.com/xm3u8/7edfd47924637736ec02cb424a0930fb318840a1f7c6c90fadc734b8ecc9e9f19921f11e97d0da21.m3u8",
        },
        {
          id: "3",
          title: "标题3",
          image: "v-thumbnail.jpg",
          video:
            "https://m3u.haiwaikan.com/xm3u8/2216440987dd8f084c3599a72cf29410ff155f84381915bba55989e7b829033a9921f11e97d0da21.m3u8",
        },
        {
          id: "4",
          title: "标题4",
          image: "v-thumbnail.jpg",
          video:
            "https://m3u.haiwaikan.com/xm3u8/3eb85c915e68688f759b8db6f37be15221a8052dccff5ebf200b422b7a7261e39921f11e97d0da21.m3u8",
        },
        {
          id: "5",
          title: "标题5",
          image: "v-thumbnail.jpg",
          video:
            "https://m3u.haiwaikan.com/xm3u8/d30f81cf12682bdac819d14dc0b945bdabaa1bf6f391771dc0ca187982fc224e9921f11e97d0da21.m3u8",
        },
        {
          id: "6",
          title: "标题6",
          image: "v-thumbnail.jpg",
          video:
            "https://m3u.haiwaikan.com/xm3u8/ec2445bbbf267a97271ab4aca2e9ae5af86b4bea8956ac6db9f127dd7865863a9921f11e97d0da21.m3u8",
        },
        {
          id: "7",
          title: "标题7",
          image: "v-thumbnail.jpg",
          video:
            "https://m3u.haiwaikan.com/xm3u8/87179e9173db39d9bf5d766685e9bd9d62e3e6e7e3bd3c3b0306eec4e1e8787b9921f11e97d0da21.m3u8",
        },
        {
          id: "8",
          title: "标题8",
          image: "v-thumbnail.jpg",
          video:
            "https://m3u.haiwaikan.com/xm3u8/2e30aff0e15a86f1789f61bb79fc709b8458a039d2fb37e113015281d8d36b7f9921f11e97d0da21.m3u8",
        },
        {
          id: "9",
          title: "标题9",
          image:
            "https://img.liangzipic.com/upload/vod/20221021-1/99b26389525118e26760c5832d312302.jpg",
          video:
            "https://m3u.haiwaikan.com/xm3u8/c334c822c4fe79989266090024080c1e013f617b9eb98510880426c70ff7d2169921f11e97d0da21.m3u8",
        },
      ],
    };
  },
  mounted() {
    const { video, title, image } = this.videos[0];
    this.onClick(video, title, image);
  },
});
</script>

<style>
/* Optional scoped styles */
.headline {
  font-size: 15px;
  color: white;
  margin-bottom: 10px;
}
</style>
