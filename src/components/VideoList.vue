<template>
  <ul class="list-group col-md-4">
    <VideoListItem
      v-bind:key="video.id.videoId"
      v-for="video in videos"
      :video="video"
      @videoSelect="onVideoSelect"
    />
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem.vue";
export default {
  name: "VideoList",
  props: ["videos"],
  components: { VideoListItem },
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSelect", video);
    }
  }
};
</script>
