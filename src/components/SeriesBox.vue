<script>
export default {
    name: "SeriesBox",
    props: ["dettagliSeries"],
    data() {
        return {
            lang: "",
            langsrc: "",
            showImage: false,
            imgshow: "",
            textshow: ""
        };
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
                this.lang = "JP";
            } else {
                this.lang = this.dettagliSeries.original_language.toUpperCase();
            }
        },
        imgshowtrue() {
            this.imgshow = "imgshow"
            this.textshow = "textshow"
        },
        imgshowfalse() {
            this.imgshow = ""
            this.textshow = ""
        },
    }
};
</script>

<template>
    <div id="seriesmbox" class="text-center" @mouseenter="imgshowtrue()" @mouseleave="imgshowfalse()">
        <div class="hover-container" :class="textshow">
            <span class="h4">Titolo:</span>
            <span>{{ dettagliSeries.name }}</span>
            <span class="h4">Titolo originale:</span>
            <span>{{ dettagliSeries.original_name }}</span>
            <span class="h4">Lingua:</span>
            <span><img :src="langsrc"></span>
            <span class="h4">Voto:</span>
            <span>{{ dettagliSeries.vote_average }}</span>
        </div>
        <div id="imgcont" :class="imgshow">
            <img src="https://image.tmdb.org/t/p/w500/a79slhzBzqMq1YG6PereCAGUfAN.jpg" alt="" />
        </div>
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

    .hover-container {
        display: flex;
        flex-direction: column;
        justify-content: center;

    }

    .textshow {
        display: none !important;
    }

    .imgshow {
        display: block !important;
    }

    #imgcont {
        height: 100%;
        display: none;

        img {
            width: 100%;
            height: 100%;
        }
    }

}
</style>