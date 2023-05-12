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
  height: 10vh;
  padding: 10px;
  display: flex;
  align-items: center;

  #searchbar {
    width: 500px;

    span {
      cursor: pointer;
    }
  }
}
</style>
