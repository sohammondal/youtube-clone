<template>
  <div class="col-md-8" v-if="video">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe class="embed-responsive-item" :src="videoUrl" allowfullscreen></iframe>
    </div>
    <div class="details border rounded p-3">
      <h4>{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
const BASE_YT_URL = "https://www.youtube.com/embed/";
export default {
  name: "VideoDetail",
  props: {
    video: {
      type: Object,
      required: false
    }
  },
  computed: {
    videoUrl: function() {
      return `${BASE_YT_URL}/${this.video.id.videoId}`;
    }
  }
};
</script>

