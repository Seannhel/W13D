
<template>
  <div id="app">
    <header>
      <h1>♫ SoundWave 2.0</h1>
      <span>Vue Music Manager</span>
    </header>

    <main>
      <h2>Your Music, Your Rules 🎵</h2>
      <p class="subtitle">
        Add songs to your playlist and choose what plays next.
      </p>

      <div class="dashboard">
        <SongList
          :songs="songs"
          @add-song="addToPlaylist"
        />

        <PlayList
          :songs="playlist"
          :activeSongId="nowPlaying ? nowPlaying.song_id : null"
          @play-song="playSong"
        />

        <NowPlaying :song="nowPlaying" />
      </div>
    </main>

    <footer>SoundWave 2.0 | Built with Vue.js</footer>
  </div>
</template>

<script>
import SongList from "./components/SongList.vue";
import PlayList from "./components/PlayList.vue";
import NowPlaying from "./components/NowPlaying.vue";

export default {
  name: "App",
  components: {
    SongList,
    PlayList,
    NowPlaying,
  },
  data() {
    return {
      songs: [
        {
          title: "Midnight Drive",
          artist: "Nova Echo",
          song_id: 1,
          image_url: "https://placehold.co/300x300/6d28d9/ffffff.png?text=Midnight+Drive",
        },
        {
          title: "Ocean Lights",
          artist: "Luna Bloom",
          song_id: 2,
          image_url: "https://placehold.co/300x300/0369a1/ffffff.png?text=Ocean+Lights",
        },
        {
          title: "City Dreams",
          artist: "Atlas Waves",
          song_id: 3,
          image_url: "https://placehold.co/300x300/be185d/ffffff.png?text=City+Dreams",
        },
        {
          title: "Golden Hour",
          artist: "Solar Sky",
          song_id: 4,
          image_url: "https://placehold.co/300x300/b45309/ffffff.png?text=Golden+Hour",
        },
      ],
      playlist: [],
      nowPlaying: null,
    };
  },
  methods: {
    addToPlaylist(song) {
      const exists = this.playlist.some(
        (item) => item.song_id === song.song_id
      );

      if (!exists) {
        this.playlist.push(song);
      }
    },
    playSong(song) {
      this.nowPlaying = song;
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #0f172a;
  color: white;
}

header {
  background: #1e293b;
  padding: 22px 6%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

header h1 {
  color: #a78bfa;
  margin: 0;
}

header span, .subtitle, footer {
  color: #94a3b8;
}

main {
  max-width: 1250px;
  margin: auto;
  padding: 50px 20px;
}

main > h2, .subtitle {
  text-align: center;
}

.subtitle {
  margin-bottom: 40px;
}

.dashboard {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 20px;
}

.panel {
  background: #1e293b;
  padding: 22px;
  border-radius: 14px;
  min-width: 0;
}

.panel h2 {
  font-size: 21px;
  margin: 0 0 20px;
}

footer {
  text-align: center;
  padding: 35px;
}

@media (max-width: 950px) {
  .dashboard {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 550px) {
  header {
    flex-direction: column;
    gap: 10px;
  }
}
</style>
