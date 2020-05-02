<template>
  <div class="container">
    <SearchBar @termChange="onTermChange" />
    <div class="row">
      <VideoDetail :video="selectedVideo" />
      <VideoList @videoSelect="onVideoSelect" :videos="videos" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";

const API_KEY = "AIzaSyCn9X2LDd9WAQgBAyhFGirv3ngHKlnyXNU";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data: () => ({
    videos: [],
    selectedVideo: null
  }),
  methods: {
    onTermChange: async function(serachTerm) {
      try {
        const { data } = await axios.get(
          "https://www.googleapis.com/youtube/v3/search",
          {
            params: {
              key: API_KEY,
              type: "video",
              part: "snippet",
              q: serachTerm
            }
          }
        );
        // console.log(data.items[0].snippet);
        this.videos = data.items;
      } catch (error) {
        console.error(error.message);
      }
    },
    onVideoSelect: function(video) {
      console.log(video);
      this.selectedVideo = video;
    }
  }
};
</script>