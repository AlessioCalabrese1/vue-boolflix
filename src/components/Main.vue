<template>
<div>
    <MovieList :filteredMovies="filteredMovies" />
    <TVshowList :filteredTvShows="filteredTvShows" />
</div>

</template>

<script>
import MovieList from './MovieList.vue';
import TVshowList from './TVshowList.vue';
export default {
    props: {
        filteredMovies: {
            type: Array,
            required: true
        },
        filteredTvShows: {
            type: Array,
            required: true
        },
    },
    components: { MovieList, TVshowList }
}
</script>

<style>

</style>