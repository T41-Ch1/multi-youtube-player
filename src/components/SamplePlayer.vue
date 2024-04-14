<template>
  <div>
    <div ref="player"></div>
    <div>
      <el-input
        v-model="videoId"
        style="width: 300px"
        placeholder="YouTubeのURLを入力してください"
      />
      <el-button @click="getVideo" type="success">動画を取得</el-button>
    </div>
  </div>
</template>

<script setup lang>
import { ref, onMounted } from "vue";
import YouTubePlayer from "youtube-player";
import "element-plus/dist/index.css";
import { ElInput, ElButton } from "element-plus";

const player = ref(null);
const videoId = ref(null);

const extractVideoId = (url) => {
  const youtubeUrlPrefix = "https://www.youtube.com/watch?v=";
  const videoId = url.replace(youtubeUrlPrefix, "");
  return videoId;
};

const getVideo = () => {
  player.value = YouTubePlayer(player.value, {
    videoId: extractVideoId(videoId.value),
    playerVars: {
      autoplay: 0,
    },
  });
};

onMounted(() => {
  getVideo;
});
</script>
