<template>
<div>
    <MovieList :filteredElements="filteredElements" />
</div>

</template>

<script>
import MovieList from './MovieList.vue';
export default {
    props: {
        filteredElements: {
            type: Array,
            required: true
        }
    },
    components: { MovieList }
}
</script>

<style>

</style>