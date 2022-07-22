<template>
  <div id="app">
    <Header @filters="getMoviesAndTvShows" />
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
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.keyAPI}&query=${filter}&language=${this.userLanguage}`)
      .then( (result) => {
        console.log(result.data.results);
        this.filteredMovies=result.data.results;
      })
      .catch((error) => {
        console.warn("Errore nell'interfacciamento all'API!")
        console.warn(error);
      });

      setTimeout(()=>{
        axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.keyAPI}&query=${filter}&language=${this.userLanguage}`)
          .then((result) => {
            console.log(result.data.results);
            this.filteredTvShows = result.data.results;
          })
          .catch((error) => {
            console.warn("Errore nell'interfacciamento all'API!")
            console.warn(error);
          });
      }, 1000)
      
    },
  },

  created(){
    
  }
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";


</style>
