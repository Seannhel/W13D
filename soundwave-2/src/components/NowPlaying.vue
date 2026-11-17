
<template>
  <section class="panel now-playing">
    <h2>🎧 NowPlaying</h2>

    <div v-if="song" class="selected">
      <img :src="song.image_url" :alt="song.title" />

      <p class="status">NOW SELECTED</p>

      <h3>{{ song.title }}</h3>
      <p>{{ song.artist }}</p>
      <span>Song ID: {{ song.song_id }}</span>
    </div>

    <div v-else class="empty">
      <div class="icon">♫</div>
      <h3>Nothing Playing</h3>
      <p>Choose a song from your playlist to see it here!</p>
    </div>
  </section>
</template>

<script>
export default {
  name: "NowPlaying",
  props: {
    song: {
      type: Object,
      default: null,
    },
  },
};
</script>

<style scoped>
.now-playing {
  text-align: center;
}

.selected {
  padding: 20px 0;
}

.selected img {
  width: 220px;
  max-width: 100%;
  aspect-ratio: 1;
  object-fit: cover;
  border-radius: 14px;
}

.status {
  color: #a78bfa;
  font-size: 12px;
  font-weight: bold;
  margin-top: 25px;
}

h3 {
  font-size: 22px;
  margin-bottom: 10px;
}

.selected p {
  color: #cbd5e1;
}

.selected span {
  color: #94a3b8;
  font-size: 13px;
}

.empty {
  padding: 65px 10px;
}

.icon {
  font-size: 65px;
  color: #a78bfa;
}

.empty p {
  color: #94a3b8;
  line-height: 1.6;
}
</style>
