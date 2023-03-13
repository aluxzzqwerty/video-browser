<template>
  <div class="container">
    <SearchBar @termChange="onTermChange" />
    <div class="row">
      <VideoDetail :video="selectedVideo" />
      <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
    </div>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue";
import youtube from "./apis/youtube";
import VideoList from "./components/VideoList.vue";
import VideoDetail from "./components/VideoDetail.vue";

export default {
  components: { SearchBar, VideoList, VideoDetail },
  name: "App",
  data: function () {
    return { videos: [], selectedVideo: null };
  },
  methods: {
    onTermChange(searchTerm) {
      youtube
        .get("/search", {
          params: {
            q: searchTerm,
          },
        })
        .then((response) => (this.videos = response.data.items));
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
  },
};
</script>
