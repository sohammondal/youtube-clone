<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";

const API_KEY = "AIzaSyCGxnljVKRHoeqnLOZJcMObJLpAOmek5MY";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList
  },
  data: () => ({
    videos: []
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
        console.error(error);
      }
    },
    onVideoSelect: function(video) {
      console.log(video);
    }
  }
};
</script>