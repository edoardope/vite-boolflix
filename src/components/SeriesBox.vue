<script>

export default {
    name: "SeriesBox",
    props: ['dettagliSeries'],
    data() {
        return {
            lang: "",
            langsrc: ""
        }
    },
    mounted() {
        this.adattamentolang();
        this.langsrc = `https://flagsapi.com/${this.lang}/shiny/64.png`;
    },
    methods: {
        adattamentolang() {
            if (this.dettagliSeries.original_language.toUpperCase() === "EN") {
                this.lang = "GB";
            } else if (this.dettagliSeries.original_language.toUpperCase() === "JA") {
                this.lang = "JP"
            } else {
                this.lang = this.dettagliFilm.original_language.toUpperCase();
            }
        }
    }
}
</script>

<template>
    <div id="seriesmbox" class="text-center">
        <span class="h4">Titolo:</span>
        <span>{{ dettagliSeries.name }}</span>
        <span class="h4">Titolo originale:</span>
        <span>{{ dettagliSeries.original_name }}</span>
        <span class="h4">Lingua:</span>
        <span><img :src="langsrc"></span>
        <span class="h4">Voto:</span>
        <span>{{ dettagliSeries.vote_average }}</span>
    </div>
</template>

<style lang="scss" scoped>
#seriesmbox {
    min-width: calc(90% / 6);
    margin-left: 2%;
    height: 100%;
    border: 1px solid black;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
</style>