<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail :videoToPlay="this.selectedVideo1"/>
      <VideoList @videoSelected="onVideoSelectedToPlay" :videoList="videos"></VideoList>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";
const API_KEY = "";
export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return { videos: [], selectedVideo1: null };
  },
  methods: {
    onVideoSelectedToPlay(video) {
      this.selectedVideo1 = video;
      /* eslint-disable no-console */
      console.log(video, "video");
    },
    onTermChange(searchTerm) {
      /* eslint-disable no-console */
      console.log(searchTerm);
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        .then(response => {
          this.videos = response.data.items;
        });
    }
  }
};
</script>
