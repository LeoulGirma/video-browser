<template>
  <li class="list-group-item media" @click="onVideoselect ">
    <img class="mr-3" :src="thumbnailUrl" alt />
    <div class="media-body">{{video.snippet.title}}</div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoselect() {
      this.$emit("videoSelected", this.video);
    }
  }
};
</script>

<style scoped>
li {
  display: flex;
}
li:hover {
  background: rgb(241, 241, 241);
}
</style>