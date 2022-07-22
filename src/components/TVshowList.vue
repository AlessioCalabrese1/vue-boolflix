<template>
  <div>
    <Card v-for="tvShow in filteredTvShows" :key="tvShow.id" :cardElement="tvShow" :cardElementType="'tvShow'" />
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