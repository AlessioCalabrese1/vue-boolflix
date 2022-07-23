<template>
  <div class="d-flex flex-wrap">
    <Card v-for="movie in filteredMovies" :key="movie.id" :cardElement="movie" :cardElementType="'movie'" />
  </div>
</template>

<script>
import Card from './Card.vue';
export default {
    props:{
        filteredMovies:{
            type: Array,
            required: true
        }
    },

    components: { Card }
}
</script>

<style>

</style>