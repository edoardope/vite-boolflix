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

    }
}
</script>

<template>
    <div id="maincont">
        <SeriesBox v-for="(element, index) in this.store.SearchedSeries" :key="index" :seriesIndex="index"
            :dettagliSeries="element" />
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