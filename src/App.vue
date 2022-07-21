<template>
  <div id="app">
    <Header @filters="getMovies" />
    <Main :filteredElements="filteredElements" />
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
      filteredElements: [],
      userLanguage: "it"
    }
  },

  components: {
    Header,
    Main
  },

  methods:{
    getMovies(filter){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.keyAPI}&query=${filter}&language=${this.userLanguage}`)
      .then( (result) => {
        console.log(result.data.results);
        this.filteredElements=result.data.results;
      })
      .catch((error) => {
        console.warn("Errore nell'interfacciamento all'API!")
        console.warn(error);
      })
    },
  },

  created(){
    
  }
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";


</style>
