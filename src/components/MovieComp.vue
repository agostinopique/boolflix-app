<template>
    <div class="movie-container">
        <h1 class="text-light">Film</h1>
        <div class="card-container">

            <CardComp 
                v-for="movie in MovieArr"
                :key="movie.id"
                :MovieCard="movie"
            />

        </div>
    </div>
</template>

<script>
import CardComp from './CardComp.vue';

export default {
    name: 'MovieComp',
    components:{
        CardComp
    },
    props: {
        MovieArr: Array
    }
}
</script>

<style lang="scss" scoped>
.movie-container h1{
    padding-left: 10px;
}
.card-container{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}
</style>