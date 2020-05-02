<template>
  <div class="col-md-4">
    <ul class="list-group">
      <VideoListItem
        v-for="video in videos"
        :key="video.etag"
        :video="video"
        @videoSelect="onVideoSelect"
      />
    </ul>
  </div>
</template>

<script>
import VideoListItem from "./VideoListItem";
export default {
  name: "VideoList",
  props: {
    videos: Array
  },
  components: {
    VideoListItem
  },
  methods: {
    onVideoSelect: function(video) {
      this.$emit("videoSelect", video);
    }
  }
};
</script>

<style>
</style>