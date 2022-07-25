<template>
    <div class="card position-relative">
        <img :src="`https://image.tmdb.org/t/p/w342${this.cardElement.poster_path}`" class="card-img-top" alt="immagine">
        <div class="card-body" v-if="cardElementType === 'movie'">
            <p class="card-text"><span>Title:</span> {{ cardElement.title }}</p>
            <p class="card-text"><span>Original Title:</span> {{ cardElement.original_title }}</p>
            <div class="flag">
                <img class="img-fluid" :src="require(`../assets/flags/${showFlag(cardElementType, cardElement.original_language)}.png`)" alt="flag">
            </div>
            <p class="card-text">
                <span>Vote:</span>  
                <!-- <i class="fa-solid fa-star" v-for="(star, index) in voteStarCalculate(cardElement.vote_average)" :key="index"></i>
                <i class="fa-regular fa-star" v-for="(star, index) in voteStarEmptyCalculate(cardElement.vote_average)" :key="index"></i> -->
            </p>
            <p class="card-text"><span>Overview:</span> {{ cardElement.overview }}</p>
        </div>


        <div class="card-body" v-if="cardElementType === 'tvShow'">
            <p class="card-text"><span>Title:</span> {{ cardElement.name }}</p>
            <p class="card-text"><span>Original Title:</span> {{ cardElement.original_name }}</p>
            <div class="flag">
                <img class="img-fluid" :src="require(`../assets/flags/${showFlag(cardElementType, cardElement.origin_country)}.png`)" alt="flag">
            </div>
            <p class="card-text">
                <span>Vote:</span>  
            </p>
            <p class="card-text"><span>Overview:</span> {{ cardElement.overview }}</p>
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

    .card{
        border: 0;
        margin: 5px;
        width: calc(20% - 10px);
        transition: all 1s;
        img{
            border-radius: 0px;
            height: 100%;
        }
    }

    .card:hover .card-body{
        display: block;
    }

    .card-body{
            background-color: black;
            color: white;
            display: none;
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            p{
                margin: 0;
            }
        }

    .card-text{
        span{
            font-weight: bold;
        }
    }
    .flag{
        width: 20px;
    }
</style>