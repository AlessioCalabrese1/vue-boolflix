<template>
  <div class="d-flex flex-wrap w-100 position-relative">
    <Card v-for="(movie, index) in filteredMovies" :key="index + 'kla'" :cardElement="movie" :cardElementType="'movie'" />
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