<script>
import SeriesBox from './SeriesBox.vue';
import { store } from '../store.js';

export default {
    name: "MainSeriesContainer",
    components: {
        SeriesBox,
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
    <div id="mainconts" @wheel.prevent="scrollHorizzontale($event, 'mainconts')">
        <SeriesBox v-for="(element, index) in this.store.SearchedSeries" :key="index" :seriesIndex="index"
            :dettagliSeries="element" />
    </div>
</template>

<style lang="scss" scoped>
#mainconts {
    height: 45vh;
    background-color: blue;
    padding: 5vh;
    display: flex;
    justify-content: space-between;
    overflow-x: auto;
    scrollbar-width: thin;
    scrollbar-color: transparent transparent;

}

#mainconts::-webkit-scrollbar {
    width: 6px;
    /* Adjust the width as needed */
}

#mainconts::-webkit-scrollbar-track {
    background-color: transparent;
    /* Set the track color as needed */
}

#mainconts::-webkit-scrollbar-thumb {
    background-color: transparent;

    /* Set the thumb color as needed */
}
</style>