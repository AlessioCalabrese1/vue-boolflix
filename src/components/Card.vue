<template>
    <div class="card" style="width: 18rem;">
        <img :src="`https://image.tmdb.org/t/p/w342${this.cardElement.poster_path}`" class="card-img-top" alt="immagine">
        <div class="card-body" v-if="cardElementType === 'movie'">
            <p class="card-text">{{ cardElement.title }}</p>
            <p class="card-text">{{ cardElement.original_title }}</p>
            <p class="card-text">{{ cardElement.original_language }}</p>
            <div class="flag">
                <img class="img-fluid" :src="require(`../assets/flags/${showFlag(cardElementType, cardElement.original_language)}.png`)" alt="flag">
            </div>
            <p class="card-text">{{ voteStarCalculate(cardElement.vote_average) }}</p>
            <i class="fa-solid fa-star" v-for="(star, index) in voteStarCalculate(cardElement.vote_average)" :key="index"></i>
            <i class="fa-regular fa-star" v-for="(star, index) in voteStarEmptyCalculate(cardElement.vote_average)" :key="index"></i>
        </div>


        <div class="card-body" v-if="cardElementType === 'tvShow'">
            <p class="card-text">{{ cardElement.name }}</p>
            <p class="card-text">{{ cardElement.original_name }}</p>
            <p class="card-text">{{ cardElement.original_language }}</p>
            <p class="card-text">{{ cardElement.origin_country}}</p>
            <div class="flag">
                <img class="img-fluid" :src="require(`../assets/flags/${showFlag(cardElementType, cardElement.origin_country)}.png`)" alt="flag">
            </div>
            <p class="card-text">{{ voteStarCalculate(cardElement.vote_average) }}</p>
            <i class="fa-solid fa-star" v-for="(star, index) in voteStarCalculate(cardElement.vote_average)" :key="index"></i>
            <i class="fa-regular fa-star" v-for="(star, index) in voteStarEmptyCalculate(cardElement.vote_average)" :key="index"></i>
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
            }else if(elementType === "movie"){
                for (let index = 0; index < this.flags.length; index++) {
                    if (this.flags[index].language == nationalityIdentifier) {
                        return this.flags[index].language;
                    }
                }
            }
            return this.backFallImgFlag;
        },

        voteStarCalculate(vote){
            vote = Math.ceil(vote/2);
            return vote;
        },

        voteStarEmptyCalculate(vote){
            vote = 5 - Math.ceil(vote/2);
            return vote;
        },
    }
}
</script>

<style lang="scss" scoped>

    .flag{
        width: 20px;
    }

</style>