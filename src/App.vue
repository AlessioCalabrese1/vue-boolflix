<template>
  <div id="app">
    <Header @filters="viewingFilteredContent" />
    <Main />
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
    }
  },

  components: {
    Header,
    Main
  },

  methods:{
    getMovie(){
      axios.get("https://api.themoviedb.org/3/search/movie?api_key=404b2ed5e305c129916cb234a784ab73&query=ritorno+al+futuro")
      .then( (result) => {
        console.log(result.data.results)
      })
    },

    viewingFilteredContent(filter){
      console.log(filter);
    }
  },

  created(){
    this.getMovie();
  }
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";


</style>
