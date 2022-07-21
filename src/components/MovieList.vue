<template>
  <div>
    <Card v-for="(movie, index) in filteredElements" :key="index" :movie="movie" />
  </div>
</template>

<script>
import Card from './Card.vue';
export default {
    props:{
        filteredElements:{
            type: Array,
            required: true
        }
    },

    components: { Card }
}
</script>

<style>

</style>