<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
    Header,
    Main
}
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";


</style>
