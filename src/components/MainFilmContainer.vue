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
        scrollHorizzontale(e, elementHtml) {
            const container = document.getElementById(elementHtml)

            if (e.deltaY > 0) {
                container.scrollLeft += 100
            } else {
                container.scrollLeft -= 100
            }
        }
    }
}
</script>

<template>
    <span class="text-white h3">Film:</span>
    <div id="maincontf" @wheel.prevent="scrollHorizzontale($event, 'maincontf')">
        <FilmBox v-for="(element, index) in this.store.SearchedFilm" :key="index" :filmIndex="index"
            :dettagliFilm="element" />
    </div>
</template>

<style lang="scss" scoped>
span {
    display: block;
    background-color: black;
    margin-bottom: 0px;
    padding-left: 80px;
    padding-top: 100px;
}

#maincontf {
    height: 500px;
    background-color: black;
    padding: 5vh;
    display: flex;
    justify-content: space-between;
    overflow-x: auto;
    scrollbar-width: thin;
    scrollbar-color: transparent transparent;

}

#maincontf::-webkit-scrollbar {
    width: 6px;
    /* Adjust the width as needed */
}

#maincontf::-webkit-scrollbar-track {
    background-color: transparent;
    /* Set the track color as needed */
}

#maincontf::-webkit-scrollbar-thumb {
    background-color: transparent;

    /* Set the thumb color as needed */
}
</style>