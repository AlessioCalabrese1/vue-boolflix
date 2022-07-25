<template>
  <div class="d-flex flex-wrap w-100 position-relative">
    <Card v-for="(tvShow, index) in filteredTvShows" :key="index + 'cx'" :cardElement="tvShow" :cardElementType="'tvShow'" />
  </div>
</template>

<script>
import Card from './Card.vue';
export default {
    props:{
        filteredTvShows:{
            type: Array,
            required: true
        }
    },

    components: { Card }
}
</script>

<style>

</style>