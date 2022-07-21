<template>
    <div class="card" style="width: 18rem;">
        <!-- <img src="..." class="card-img-top" alt="..."> -->
        <div class="card-body" v-if="cardElementType === 'movie'">
            <p class="card-text">{{ cardElement.title }}</p>
            <p class="card-text">{{ cardElement.original_title }}</p>
            <p class="card-text">{{ cardElement.original_language }}</p>
            <p class="card-text">{{ cardElement.vote_average }}</p>
        </div>

        <div class="card-body" v-if="cardElementType === 'tvShow'">
            <p class="card-text">{{ cardElement.name }}</p>
            <p class="card-text">{{ cardElement.original_name }}</p>
            <p class="card-text">{{ cardElement.original_language }}</p>
            <p class="card-text">{{ cardElement.vote_average }}</p>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        cardElement: {
            type: Object,
            required: true
        },

        cardElementType:{
            type: String,
            required: true
        }
    }
}
</script>

<style>
</style>