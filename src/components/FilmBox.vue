<script>
export default {
    name: "FilmBox",
    props: ['dettagliFilm', 'filmIndex'],

    data() {
        return {
            lang: "",
            langsrc: "",
            imgshow: "",
            textshow: "",
            imgLink: `https://image.tmdb.org/t/p/w500/${this.dettagliFilm.backdrop_path}`,
            convertedVote: ""
        }
    },

    mounted() {
        this.adattamentolang();
        this.langsrc = `https://flagsapi.com/${this.lang}/shiny/64.png`;
        this.convertVote()
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
        },
        imgshowtrue() {
            this.imgshow = "imgshow"
            this.textshow = "textshow"
        },
        imgshowfalse() {
            this.imgshow = ""
            this.textshow = ""
        },
        convertVote() {
            this.convertedVote = Math.ceil(this.dettagliFilm.vote_average / 2);
        }
    }
}
</script>

<template>
    <div id="filmbox" class="text-center" @mouseenter="imgshowtrue()" @mouseleave="imgshowfalse()">
        <div class="hover-container" :class="textshow">
            <span class="h4">Titolo:</span>
            <span>{{ dettagliFilm.title }}</span>
            <span class="h4">Titolo originale:</span>
            <span>{{ dettagliFilm.original_title }}</span>
            <span class="h4">Lingua:</span>
            <span><img :src="langsrc"></span>
            <span class="h4">Voto:</span>
            <span>{{ this.convertedVote }}<i class="fa-sharp fa-star"
                    :class="convertedVote >= 1 ? 'fa-solid' : 'fa-regular'"></i>
                <i class="fa-sharp fa-star" :class="convertedVote >= 2 ? 'fa-solid' : 'fa-regular'"></i><i
                    class="fa-sharp fa-star" :class="convertedVote >= 3 ? 'fa-solid' : 'fa-regular'"></i><i
                    class="fa-sharp fa-star" :class="convertedVote >= 4 ? 'fa-solid' : 'fa-regular'"></i><i
                    class="fa-sharp fa-star" :class="convertedVote >= 5 ? 'fa-solid' : 'fa-regular'"></i></span>
        </div>
        <div id="imgcont" :class="imgshow">
            <img :src="imgLink" alt="" />
        </div>
    </div>
</template>

<style lang="scss" scoped>
#filmbox {
    min-width: 300px;
    height: 100%;
    border: 1px solid black;
    display: flex;
    flex-direction: column;
    justify-content: center;
    background-color: white;

    .hover-container {
        display: none;
        flex-direction: column;
        justify-content: center;

    }

    .imgshow {
        display: none !important;
    }

    .textshow {
        display: flex !important;
    }

    #imgcont {
        height: 100%;
        display: block;

        img {
            width: 100%;
            height: 100%;
        }
    }
}
</style>