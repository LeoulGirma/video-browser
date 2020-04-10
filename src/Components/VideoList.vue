<template>
  <div class="col-md-4">
    <ul class="list-group" v-for="video in videoList" :key="video.etag">
      <VideoListItem @videoSelected="onVideoSelect" :video="video" />
    </ul>
  </div>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideoList",
  props: {
    videoList: Array
  },
  data() {
    return {
      title: []
    };
  },
  components: {
    VideoListItem
  },
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSelected", video);
    }
  }
};
</script>

<style>
</style>