
<template>
  <section class="panel">
    <h2>🎵 SongList</h2>
    <p>Choose songs to add.</p>

    <div class="songs">
      <button
        v-for="song in songs"
        :key="song.song_id"
        class="song"
        @click="$emit('add-song', song)"
      >
        <img :src="song.image_url" :alt="song.title" />

        <div class="info">
          <strong>{{ song.title }}</strong>
          <span>{{ song.artist }}</span>
        </div>

        <span class="add">+</span>
      </button>
    </div>
  </section>
</template>

<script>
export default {
  name: "SongList",
  props: {
    songs: {
      type: Array,
      required: true,
    },
  },
  emits: ["add-song"],
};
</script>

<style scoped>
p {
  color: #94a3b8;
  font-size: 14px;
}

.songs {
  display: grid;
  gap: 12px;
  margin-top: 25px;
}

.song {
  display: flex;
  align-items: center;
  gap: 12px;
  background: #0f172a;
  border: 1px solid #334155;
  border-radius: 10px;
  padding: 10px;
  width: 100%;
  color: white;
  cursor: pointer;
  text-align: left;
}

.song:hover {
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

.add {
  color: #a78bfa;
  font-size: 24px;
}
</style>
