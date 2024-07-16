<template>
  <v-app class="app-background">
    <!-- App Bar -->
    <v-appbar />

    <!-- Content Area -->
    <v-main class="container">
      <v-title-section />
      <v-video-player
        :videoUrl="videoUrl"
        :caption="caption"
        :preview="preview"
      />
      <v-container style="text-align: center">
        <v-btn class="save-btn" size="md" rounded="xl"
          >保存到桌面 观看更多视频</v-btn
        >
      </v-container>
      <v-video-list @click="changeVideo" />
    </v-main>

    <!-- Footer -->
    <v-appfooter />
  </v-app>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import AppBar from "@/components/AppBar.vue";
import TitleSection from "@/components/TitleSection.vue";
import VideoPlayer from "@/components/VideoPlayer.vue";
import VideoList from "@/components/VideoList.vue";
import AppFooter from "@/components/AppFooter.vue";

export default defineComponent({
  name: "App",
  components: {
    "v-appbar": AppBar,
    "v-video-player": VideoPlayer,
    "v-title-section": TitleSection,
    "v-video-list": VideoList,
    "v-appfooter": AppFooter,
  },
  data() {
    return {
      videoUrl: "",
      caption: "",
      preview: "",
    };
  },
  methods: {
    changeVideo(videoUrl: string, caption: string, preview: string) {
      this.videoUrl = videoUrl;
      this.caption = caption;
      this.preview = preview;
    },
  },
});
</script>

<style>
/* Add custom styles here */
.app-background {
  background-color: #131313;
}

.container {
  display: grid;
}

.save-btn {
  font-size: 16px;
  padding: 7px 50px;
  font-weight: bold;
  background: linear-gradient(90deg, #61feee, #01d6be);
}
</style>
