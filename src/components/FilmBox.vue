<script>
export default {
    name: "FilmBox",
    props: ['dettagliFilm', 'filmIndex'],

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
            if (this.dettagliFilm.original_language.toUpperCase() === "EN") {
                this.lang = "GB";
            } else if (this.dettagliFilm.original_language.toUpperCase() === "JA") {
                this.lang = "JP"
            } else {
                this.lang = this.dettagliFilm.original_language.toUpperCase();
            }
        }
    }
}
</script>

<template>
    <div id="filmbox" class="text-center">
        <span class="h4">Titolo:</span>
        <span>{{ dettagliFilm.title }}</span>
        <span class="h4">Titolo originale:</span>
        <span>{{ dettagliFilm.original_title }}</span>
        <span class="h4">Lingua:</span>
        <span><img :src="langsrc"></span>
        <span class="h4">Voto:</span>
        <span>{{ dettagliFilm.vote_average }}</span>
    </div>
</template>

<style lang="scss" scoped>
#filmbox {
    min-width: calc(90% / 6);
    margin-left: 2%;
    height: 100%;
    border: 1px solid black;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
</style>