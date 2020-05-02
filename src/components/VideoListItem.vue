<template>
  <li class="list-group-item media d-flex" @click="onVideoSelect">
    <img class="mr-3" :src="thumbnailUrl" alt />
    <div class="media-body">
      <h5 class="mt-0 mb-1">{{ video.snippet.title }}</h5>
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: {
    video: Object
  },
  computed: {
    thumbnailUrl: function() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect: function() {
      this.$emit("videoSelect", this.video);
    }
  }
};
</script>

<style scoped>
li {
  cursor: pointer;
}
li:hover {
  background-color: #eee;
}
</style>