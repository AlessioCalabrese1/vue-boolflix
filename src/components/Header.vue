<template>
    <header class="d-flex justify-content-between p-3">

        <div class="logo">
            Boolfix
        </div>

        <div class="input-group">
            <button class="btn btn-outline-secondary" type="button" id="button-addon1" @click="$emit('filters', filter)">
                <i class="fa-solid fa-magnifying-glass"></i>
            </button>
            <input type="text" class="form-control" placeholder="Title" aria-label="Example text with button addon" aria-describedby="button-addon1"
            v-model="filter" @keyup.enter="$emit('filters', filter)">
        </div>
    </header>
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
@import "../styles/variables.scss";

    header{
        background-color: $companyBackgroundColor;
    }

    .logo{
        color: $companyLogoColor;
        font-weight: 600;
        font-size: 24px;
        text-transform: uppercase;
    }

    .input-group{
        width: 20%;
        border-radius: 0;
        border: 1px solid white;

        .btn{
            border: 0;
            border-radius: 0;
            background-color: black;
        }

        input{
            border: 0 solid white;
            border-radius: 0;
            background-color: black;
            color: white;
            box-shadow: none;
        }
    }
</style>