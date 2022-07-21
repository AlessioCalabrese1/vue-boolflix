<template>
    <div class="card" style="width: 18rem;">
        <!-- <img src="..." class="card-img-top" alt="..."> -->
        <div class="card-body">
            <p class="card-text">{{ movie.title }}</p>
            <p class="card-text">{{ movie.original_title}}</p>
            <p class="card-text">{{ movie.original_language }}</p>
            <p class="card-text">{{ movie.vote_average}}</p>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        movie: {
            type: Object,
            required: true
        }
    }
}
</script>

<style>
</style>