<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import MainFilmContainer from './components/MainFilmContainer.vue';
import MainSeriesContainer from './components/MainSeriesContainer.vue'
import { store } from './store.js';

export default {
  name: "App",
  components: {
    SearchBar,
    MainFilmContainer,
    MainSeriesContainer
  },
  data() {
    return {
      store,
    }
  },
  created() {
    this.searchFilm();
  },
  methods: {
    searchFilm() {
      store.SearchedFilm = [];
      store.SearchedSeries = [];
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=1b27b7a0a1bb558320f18122890eab97&query=${this.store.searchText}`)
        .then(res => {
          console.log(res.data.results);
          store.SearchedFilm = res.data.results;
        })
        .catch(error => {
          console.error(errorfil);
        });
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=1b27b7a0a1bb558320f18122890eab97&query=${this.store.searchText}`)
        .then(res => {
          console.log(res.data.results);
          store.SearchedSeries = res.data.results;
        })
        .catch(error => {
          console.error(errorser);
        });
    },
    getImagePath: function (imgPath) {
      return new URL(imgPath, import.meta.url).href;
    }
  }
}
</script>

<template>
  <SearchBar @search="searchFilm()" />
  <MainFilmContainer />
  <MainSeriesContainer />
</template>

<style lang="scss">
@use 'style/main.scss' as *;
</style>
