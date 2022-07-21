<template>
    <div class="input-group mb-3">
        <button class="btn btn-outline-secondary" type="button" id="button-addon1" @click="$emit('filters', filter)">Button</button>
        <input type="text" class="form-control" placeholder="" aria-label="Example text with button addon" aria-describedby="button-addon1"
        v-model="filter" @keyup.enter="$emit('filters', filter)">
    </div>
</template>

<script>
export default {
    data: function(){
        return{
            filter: "",
        }
    }
}
</script>

<style lang="scss" scoped>

</style>