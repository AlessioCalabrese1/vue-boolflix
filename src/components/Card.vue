<template>
    <div class="card" style="width: 18rem;">
        <img :src="`https://image.tmdb.org/t/p/w342${this.cardElement.poster_path}`" class="card-img-top" alt="immagine">
        <div class="card-body" v-if="cardElementType === 'movie'">
            <p class="card-text">{{ cardElement.title }}</p>
            <p class="card-text">{{ cardElement.original_title }}</p>
            <p class="card-text">{{ cardElement.original_language }}</p>
            <p class="card-text">{{ cardElement.vote_average }}</p>
        </div>

        <div class="card-body" v-if="cardElementType === 'tvShow'">
            <p class="card-text">{{ cardElement.name }}</p>
            <p class="card-text">{{ cardElement.original_name }}</p>
            <p class="card-text">{{ cardElement.original_language }}</p>
            <p class="card-text">{{ cardElement.origin_country}}</p>
            <div class="flag">
                <img class="img-fluid" :src="require(`../assets/flags/${showFlag(cardElementType, cardElement.origin_country)}.png`)" alt="flag">
            </div>
            <p class="card-text">{{ cardElement.vote_average }}</p>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        cardElement: {
            type: Object,
            required: true
        },

        cardElementType:{
            type: String,
            required: true
        }
    },

    data: function(){
        return{
            flags:[
                {
                    language: "it",
                    country: "IT",
                    flagImg: "/assets/flags/ITflag.png"
                },
                {
                    language: "en",
                    country: "US",
                    flagImg: "/assets/flags/USAflag.png"
                },
            ],

            backFallImgFlag: "fallback",
            urlIm: "",
        }
    },

    methods:{
        showFlag(elementType, nationalityIdentifier){
            if (elementType === "tvShow") {
                console.log(nationalityIdentifier)
                for (let index = 0; index < this.flags.length; index++) {
                    if (this.flags[index].country == nationalityIdentifier) {
                        return this.flags[index].language;
                    }
                }
                return this.backFallImgFlag;
            }
        },
    }
}
</script>

<style lang="scss" scoped>

    .flag{
        width: 20px;
    }

</style>