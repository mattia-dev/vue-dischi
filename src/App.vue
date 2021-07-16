<template>
  <div id="app">
    <Loader v-if="this.albums.length === 0" />
    <div v-if="this.filteredAlbums.length === 0" class="alert-container">
      <div class="alert">Nothing found. Try another search.</div>
    </div>
    <Header :albums="albums" @select="filterAlbumsGenre" @search="filterAlbumsArtist" />
    <Main :albums="filteredAlbums" />
  </div>
</template>

<script>
import axios from 'axios'
import Loader from './components/Loader.vue'
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Loader,
    Header,
    Main
  },
  data() {
    return {
      albums: [],
      filteredAlbums: [],
    }
  },
  created() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((response) => {
      this.albums = response.data.response;
      this.filteredAlbums = this.albums;
    })
  },
  methods: {
    filterAlbumsGenre: function(selectedGenre) {
      if (selectedGenre !== "All") {
        this.filteredAlbums = [];
        this.albums.forEach(album => {
          if (album.genre === selectedGenre) {
            this.filteredAlbums.push(album);
          }
        });
      } else {
        this.filteredAlbums = this.albums;
      }
      
    },
    filterAlbumsArtist: function(searchedArtist) {
      if (searchedArtist.toLowerCase().trim() !== "") {
        this.filteredAlbums = [];
        this.albums.forEach(album => {
          if (album.author.toLowerCase().includes(searchedArtist.toLowerCase().trim())) {
            this.filteredAlbums.push(album);
          }
        });
        searchedArtist = "";
      } else {
        this.filteredAlbums = this.albums;
      }
      
    },
  }
}
</script>

<style lang="scss">
@import "./style/App.scss"
</style>
