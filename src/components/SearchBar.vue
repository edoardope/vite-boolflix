<script>
import { store } from '../store.js';

export default {
  name: "SearchBar",
  data() {
    return {
      store,
    }
  },
  methods: {

  }
}
</script>

<template>
  <div>
    <div>
      <img src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="">
    </div>
    <div id="searchbar" class="input-group mb-3">
      <span @click="$emit('search')" class="input-group-text" id="inputGroup-sizing-default">Search</span>
      <input v-model="store.searchText" type="text" class="form-control" aria-label="Sizing example input"
        aria-describedby="inputGroup-sizing-default">
    </div>
  </div>
</template>

<style lang="scss" scoped>
div {
  background-color: black;
  height: 100px;
  padding-top: 50px !important;
  padding: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;

  img {
    width: 70%;
    margin-left: 60px;
  }

  #searchbar {
    width: 500px;
    padding: 0px;
    margin: 0px !important;

    span {
      cursor: pointer;
    }
  }
}
</style>
