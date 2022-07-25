<template>
    <header class="d-flex justify-content-between p-3">
        <div class="logo">
            Boolfix
        </div>

        <select class="form-select" aria-label="Default select example" v-model="genreSelected" @change="$emit('genreInterception', genreSelected)">
            <option value="All">All</option>
            <option value="genre" v-for="genre in genres" :key="genre.id">{{genre.name}}</option>
        </select>

        <div class="input-group">
            <button class="btn btn-outline-secondary" type="button" id="button-addon1"
                @click="$emit('filters', filter)">
                <i class="fa-solid fa-magnifying-glass"></i>
            </button>
            <input type="text" class="form-control" placeholder="Title" aria-label="Example text with button addon"
                aria-describedby="button-addon1" v-model="filter" @keyup.enter="$emit('filters', filter)">
        </div>
    </header>
</template>

<script>
import axios from 'axios';

export default {
    data: function(){
        return{
            filter: "",
            genres: [],
            genreSelected: "All",
        }
    },

    methods: {
        searchGenres(){
            axios.get(`https://api.themoviedb.org/3/genre/movie/list?api_key=404b2ed5e305c129916cb234a784ab73&language=it`)
            .then((result) => {
              this.genres = result.data.genres;
            })
            .catch((error) => {
              console.warn("Errore nell'interfacciamento all'API!")
              console.warn(error);
            });
        },
    },

    created(){
        this.searchGenres();
    }
}
</script>

<style lang="scss" scoped>
@import "../styles/variables.scss";

    header{
        background-color: $companyBackgroundColor;
        width: 100%;
        position: fixed;
        top: 0;
        left: 0;
        z-index: 5;
    }

    .logo{
        color: $companyLogoColor;
        font-weight: 600;
        font-size: 24px;
        text-transform: uppercase;
    }

    .input-group{
        width: 20%;
        border-radius: 0;
        border: 1px solid white;

        .btn{
            border: 0;
            border-radius: 0;
            background-color: black;
        }

        input{
            border: 0 solid white;
            border-radius: 0;
            background-color: black;
            color: white;
            box-shadow: none;
        }
    }

    select{
        width: 20%;
    }
</style>