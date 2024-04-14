<template>
  <div>
    <div ref="player"></div>
    <button @click="playVideo">Play</button>
    <button @click="pauseVideo">Pause</button>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import YouTubePlayer from "youtube-player";

const player = ref(null);
const videoId = "HP4KmuCcQqc";

const playVideo = () => {
  player.value.playVideo();
};

const pauseVideo = () => {
  player.value.pauseVideo();
};

onMounted(() => {
  player.value = YouTubePlayer(player.value, {
    videoId: videoId,
    playerVars: {
      autoplay: 0,
    },
  });
});

onUnmounted(() => {
  player.value.destroy();
});
</script>
