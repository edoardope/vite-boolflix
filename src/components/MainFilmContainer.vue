<script>
import FilmBox from './FilmBox.vue';
import { store } from '../store.js';

export default {
    name: "MainFilmContainer",
    components: {
        FilmBox,
    },
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
    <div id="maincont">
        <FilmBox v-for="(element, index) in this.store.SearchedFilm" :key="index" :filmIndex="index"
            :dettagliFilm="element" />
    </div>
</template>

<style lang="scss" scoped>
#maincont {
    height: 45vh;
    background-color: blue;
    padding: 5vh;
    display: flex;
    justify-content: space-between;
    overflow-x: scroll;

}
</style>