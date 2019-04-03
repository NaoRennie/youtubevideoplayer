<template>
  <li class="list-group-item media" @click="onVideoSelect">
    <img class="mr-3" :src="thumnailUrl">
    <div class="media-body">{{ singleVideo.snippet.title }}</div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: {
    singleVideo: Array
  },
  computed: {
    thumnailUrl() {
      return this.singleVideo.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect() {
      this.$emit("videoSelect", this.singleVideo);
    }
  }
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
}
li:hover {
  background-color: "#eee";
}
</style>
