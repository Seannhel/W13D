
<template>
  <section class="panel">
    <h2>📋 PlayList</h2>
    <p>{{ songs.length }} songs added</p>

    <div v-if="songs.length === 0" class="empty">
      <div class="icon">♫</div>
      <h3>Your playlist is empty</h3>
      <p>Pick a song from SongList to get started!</p>
    </div>

    <div v-else class="playlist">
      <button
        v-for="song in songs"
        :key="song.song_id"
        class="track"
        :class="{ active: activeSongId === song.song_id }"
        @click="$emit('play-song', song)"
      >
        <img :src="song.image_url" :alt="song.title" />

        <div class="info">
          <strong>{{ song.title }}</strong>
          <span>{{ song.artist }}</span>
        </div>

        <span class="play">▶</span>
      </button>
    </div>
  </section>
</template>

<script>
export default {
  name: "PlayList",
  props: {
    songs: {
      type: Array,
      required: true,
    },
    activeSongId: {
      type: Number,
      default: null,
    },
  },
  emits: ["play-song"],
};
</script>

<style scoped>
p {
  color: #94a3b8;
  font-size: 14px;
}

.empty {
  text-align: center;
  padding: 55px 10px;
}

.icon {
  font-size: 55px;
  color: #a78bfa;
}

.empty h3 {
  font-size: 17px;
}

.playlist {
  display: grid;
  gap: 12px;
  margin-top: 25px;
}

.track {
  display: flex;
  align-items: center;
  gap: 12px;
  width: 100%;
  padding: 10px;
  color: white;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 10px;
  cursor: pointer;
  text-align: left;
}

.track:hover,
.track.active {
  background: #312e81;
  border-color: #a78bfa;
}

img {
  width: 55px;
  height: 55px;
  border-radius: 8px;
  object-fit: cover;
}

.info {
  flex: 1;
  min-width: 0;
}

strong {
  display: block;
  font-size: 14px;
  margin-bottom: 7px;
}

.info span {
  color: #94a3b8;
  font-size: 12px;
}

.play {
  color: #a78bfa;
}
</style>
