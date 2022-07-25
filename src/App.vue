<template>
  <div id="app">
    <Header @filters="getMoviesAndTvShows" @genreInterception="moviesAndTvShowsGenre"/>
    <Main :filteredMovies="filteredMovies" :filteredTvShows="filteredTvShows" />
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
  name: 'App',

  data: function(){
    return{
      keyAPI: "404b2ed5e305c129916cb234a784ab73",
      movies: [],
      tvShows: [],
      filteredMovies: [],
      filteredTvShows: [],
      userLanguage: "it"
    }
  },

  components: {
    Header,
    Main
  },

  methods:{
    getMoviesAndTvShows(filter){
      if (filter == "") {
        this.filteredMovies = [];
        this.filteredTvShows = [];
      }else{
        axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.keyAPI}&query=${filter}&language=${this.userLanguage}`)
          .then((result) => {
            this.movies = result.data.results;
            this.filteredMovies = this.movies;
          })
          .catch((error) => {
            console.warn("Errore nell'interfacciamento all'API!")
            console.warn(error);
          });

        setTimeout(() => {
          axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.keyAPI}&query=${filter}&language=${this.userLanguage}`)
            .then((result) => {
              this.tvShows = result.data.results;
              this.filteredTvShows = this.tvShows;
            })
            .catch((error) => {
              console.warn("Errore nell'interfacciamento all'API!")
              console.warn(error);
            });
        }, 1000);
      }
    },

    moviesAndTvShowsGenre(genre){
      if (genre == "All") {
        this.filteredMovies = this.movies;
        this.filteredTvShows = this.tvShows;
      }else{
        this.filteredMovies = [];
        console.log(this.filteredMovies);
        for (let index = 0; index < this.movies.length; index++) {
          console.log(this.movies[index].genre_ids)
          console.log(genre)
          if (this.movies[index].genre_ids.includes(genre.id)) {
            console.log("sono nell IF")
            this.filteredMovies.push(this.movies[index]);

          }
          
        }
        /* this.filteredMovies = this.movies.filter((movie) => movie.genre_ids.includes(genre.id)); */
        /* this.filteredTvShows = this.tvShows.filter((tvShow) => tvShow.genre_ids.includes(genre.id)); */
      }
    } 
  },
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";

main{
  min-height: calc(100vh - 70px);
}
</style>
