<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail :video="selectedVideo" />
      <VideoList @videoSelected="onVideoSelect" :videoList="searchResult"></VideoList>
    </div>
  </div>
</template>

<script>
import axios from "axios";

import SearchBar from "./Components/SearchBar";
import VideoList from "./Components/VideoList";
import VideoDetail from "./Components/VideoDetail";

const API_KEY = "YOUR youtube API_KEY";
export default {
  name: "App",
  data() {
    return {
      searchResult: [],
      selectedVideo: null
    };
  },
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  methods: {
    onVideoSelect(video) {
      console.log(video);
      this.selectedVideo = video;
    },
    onTermChange(searchTerm) {
      // console.log(searchTerm);
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
          this.searchResult = response.data.items;
          // console.log(this.searchResult);
        });
    }
  }
};
</script>

<style>
</style>