<template>
<main class="d-flex">
        <MovieList :filteredMovies="filteredMovies" />
        <TVshowList :filteredTvShows="filteredTvShows" />
</main>
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

<style lang="scss" scoped>
@import "../styles/variables.scss";

    main{
        margin-top: 70px;
        flex-wrap: wrap;
        background-color: $companyBackgroundColor;
        padding: 30px 50px;
    }
</style>