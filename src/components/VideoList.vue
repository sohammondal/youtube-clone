<template>
  <ul class="list-group">
    <VideoListItem v-for="video in videos" :key="video.etag" :video="video" />
  </ul>
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
  }
};
</script>

<style>
</style>